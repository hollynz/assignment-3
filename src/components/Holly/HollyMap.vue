<!-- Parent component to everything: Holly (landing) and InfoScreen!!! -->

<template>
  <div>
    <GoogleMap :mapConfig="mapConfig"/>
    <!-- <HollyLanding @$categorySelected="categorySelected" /> -->
    <HollyInfoScreen @$categorySelected="categorySelected" />
  </div>
</template>

<script>
import GoogleMap from "./GoogleMap";
import HollyLanding from "./HollyLanding.vue";
import HollyInfoScreen from "./HollyInfoScreen.vue";
import { mapSettings } from "./constants/mapSettings";

export default {
  name: "HollyMap",
  components: {
    GoogleMap,
    HollyLanding,
    HollyInfoScreen
  },
  data: function() {
    return {
      category: ""
    }
  },
  computed: {
    mapConfig() {
      return {
        ...mapSettings,
        center: { lat: -38.1368, lng: 176.2497 }
      };
    }
  },
  methods: {
    categorySelected: function(id) {
      console.log("in map: " + id);
    }
  }
};
</script>


<style scoped>

</style>