<template>
  <div class="map">
    <div class="google-map" ref="googleMap"></div>
    <template v-if="Boolean(this.google) && Boolean(this.map)">
      <slot :google="google" :map="map"/>
    </template>
    <button @click="addMarkers([{position: { lat: -38.1368, lng: 176.2497 }},{position: { lat: -38.14, lng: 176.25 }},{position: { lat: -38.13, lng: 176.23 }}])">add</button>
    <button @click="deleteMarkers">delete</button>
  </div>
</template>

<script>
import GoogleMapsApiLoader from "google-maps-api-loader";
import { API_KEY } from "./constants/config.js";

export default {
  name: "GoogleMap",
  props: {
    mapConfig: Object
  },

  data() {
    return {
      google: null,
      map: null,
      apiKey: API_KEY,
      // marker: {
      //   position: { lat: -38.1368, lng: 176.2497 }
      // },
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

  methods: {
    initializeMap() {
      const mapContainer = this.$refs.googleMap;
      this.map = new this.google.maps.Map(mapContainer, this.mapConfig);
    },
    addMarkers(locations) {
      let thisGoogleMap = this.google.maps;
      let thisMap = this.map;
      let thisMarkers = this.markers;
      $.each(locations, function(i, location) {
        let newMarker = new thisGoogleMap.Marker({
          position: location.position,
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
      thisMarkers = [];
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