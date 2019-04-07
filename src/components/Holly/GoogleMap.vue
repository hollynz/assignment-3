<template>
  <div class="map">
    <div class="google-map" ref="googleMap"></div>
    <!-- <template v-if="Boolean(this.google) && Boolean(this.map)">
      <slot :google="google" :map="map"/>
    </template>-->
  </div>
</template>

<script>
import GoogleMapsApiLoader from "google-maps-api-loader";
import { API_KEY } from "./constants/config.js";
import { CLIENT_ID } from "./constants/config.js";
import { CLIENT_SECRET } from "./constants/config.js";
import { API_CATEGORIES } from "./constants/data.js";
import { CENTER_POSITION } from "./constants/data.js";
import { CENTER_LAT_LONG } from "./constants/data.js";
import { DEFAULT_ZOOM } from "./constants/data.js";

export default {
  name: "GoogleMap",
  props: {
    mapConfig: Object,
    category: "",
    landing: false,
    markerIsActive: Boolean
  },
  data() {
    return {
      google: null,
      map: null,
      apiKey: API_KEY,
      clientID: CLIENT_ID,
      clientSecret: CLIENT_SECRET,
      markers: []
    };
  },
  async mounted() {
    const googleMapApi = await GoogleMapsApiLoader({
      apiKey: this.apiKey
    });
    this.google = googleMapApi;
    this.initializeMap();
  },
  watch: {
    category: function() {
      this.getData();
    },
    landing: function() {
      this.deleteMarkers();
      this.$emit("$landingFalse");
      this.initializeMap();
    },
    markerIsActive: function() {
      if (!this.markerIsActive) {
        this.map.setZoom(DEFAULT_ZOOM);
      }
    }
  },
  methods: {
    initializeMap() {
      const mapContainer = this.$refs.googleMap;
      this.map = new this.google.maps.Map(mapContainer, {
        zoom: DEFAULT_ZOOM,
        mapTypeControl: true,
        mapTypeControlOptions: {
          position: google.maps.ControlPosition.TOP_RIGHT
        },
        fullscreenControl: true,
        fullscreenControlOptions: {
          position: google.maps.ControlPosition.TOP_RIGHT
        },
        streetViewControl: true,
        streetViewControlOptions: {
          position: google.maps.ControlPosition.RIGHT_TOP
        },
        zoomControl: true,
        zoomControlOptions: {
          position: google.maps.ControlPosition.RIGHT_BOTTOM
        },
        center: { lat: CENTER_LAT_LONG[0], lng: CENTER_LAT_LONG[1] }
      });
      this.map.getStreetView().setOptions({
        addressControlOptions: {
          position: google.maps.ControlPosition.TOP_CENTER
        },
        panControlOptions: {
          position: google.maps.ControlPosition.RIGHT_TOP
        }
      });
    },
    getData() {
      this.$http
        .get(
          "https://api.foursquare.com/v2/venues/search?" +
            "ll=" +
            CENTER_POSITION +
            "&categoryId=" +
            API_CATEGORIES[this.category].categories +
            "&radius=50000" +
            "&client_id=" +
            this.clientID +
            "&client_secret=" +
            this.clientSecret +
            "&v=20190404"
        )
        .then(function(result) {
          this.deleteMarkers();
          this.addMarkers(result);
        });
    },
    addMarkers(data) {
      let that = this;
      let markers = data.body.response.venues;
      $.each(markers, function(i, marker) {
        let newMarker = new that.google.maps.Marker({
          position: { lat: marker.location.lat, lng: marker.location.lng },
          map: that.map
        });
        newMarker.addListener("click", function(evt) {
          // Smooth transition here somehow
          that.map.setCenter(newMarker.getPosition());
          that.map.setZoom(14);
          // that.getActivityInfo(newMarker);
          // Pass activity info to emit when it's working!!
          that.$emit("$markerClicked", "data");
        });
        that.markers.push(newMarker);
      });
    },
    deleteMarkers() {
      let that = this;
      $.each(that.markers, function(i, marker) {
        marker.setMap(null);
      });
      this.markers = [];
    }
  }
};
</script>

<style scoped>
.google-map {
  width: 100vw;
  min-height: 100vh;
  position: relative;
  z-index: 1;
  top: 0;
  left: 0;
}
</style>