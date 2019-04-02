<!-- Parent component to everything: Holly (landing) and InfoScreen!!! -->

<template>
  <div>
    <GoogleMap :mapConfig="mapConfig"/>
    <HollyLanding />
  </div>
</template>

<script>
import GoogleMap from "./GoogleMap";
import HollyLanding from "./HollyLanding.vue";
import { mapSettings } from "./constants/mapSettings";

export default {
  name: "HollyMap",
  components: {
    GoogleMap,
    HollyLanding
  },
  computed: {
    mapConfig() {
      return {
        ...mapSettings,
        center: { lat: -38.1368, lng: 176.2497 }
      };
    }
  }
};
</script>


<style>

</style>