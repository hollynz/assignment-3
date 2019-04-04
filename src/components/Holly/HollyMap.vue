<!-- Parent component to everything: Holly (landing) and InfoScreen!!! -->

<template>
  <div>
    <GoogleMap @$landingFalse="landingFalse" :landing="landing" :category="category" :mapConfig="mapConfig"/>
    <HollyLanding @$categorySelected="categorySelected" v-if="this.$parent.$data.landing"/>
    <HollyInfoScreen @$goHome="goHome" @$categorySelected="categorySelected" v-if="this.$parent.$data.info" />
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
      category: "",
      landing: false
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
      this.$parent.$data.landing = false;
      this.$parent.$data.info = true;
      this.category = id;
    },
    goHome: function() {
      this.$parent.$data.landing = true;
      this.$parent.$data.info = false;
      this.landing = true;
    },
    landingFalse: function() {
      this.landing = false;
    }
  }
};
</script>


<style scoped>

</style>