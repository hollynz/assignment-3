<template>
  <div class="map">
    <div class="google-map" ref="googleMap"></div>
    <template v-if="Boolean(this.google) && Boolean(this.map)">
      <slot :google="google" :map="map"/>
    </template>
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

export default {
  name: "GoogleMap",
  props: {
    mapConfig: Object,
    category: "",
    landing: false
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
    category() {
      this.getData();
    },
    landing() {
      this.deleteMarkers();
      this.$emit("$landingFalse");
    }
  },
  methods: {
    initializeMap() {
      const mapContainer = this.$refs.googleMap;
      this.map = new this.google.maps.Map(mapContainer, {
        zoom: 11,
        mapTypeControl: true,
        mapTypeControlOptions: {
          position: google.maps.ControlPosition.TOP_RIGHT,
        },
        fullscreenControl: true,
        fullscreenControlOptions: {
          position: google.maps.ControlPosition.TOP_RIGHT
        },
        center: { lat: CENTER_LAT_LONG[0], lng: CENTER_LAT_LONG[1] }
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
      let markers = data.body.response.venues;
      let thisGoogleMap = this.google.maps;
      let thisMap = this.map;
      let thisMarkers = this.markers;
      $.each(markers, function(i, marker) {
        let newMarker = new thisGoogleMap.Marker({
          position: { lat: marker.location.lat, lng: marker.location.lng },
          map: thisMap
        });
        thisMarkers.push(newMarker);
      });
    },
    deleteMarkers() {
      let thisMarkers = this.markers;
      $.each(thisMarkers, function(i, marker) {
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