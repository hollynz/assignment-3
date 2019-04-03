<template>
  <div class="lhs-nav">
    <Logo/>
    <div :class="{buttonsLanding: landing, buttonsInfo: info}">
      <ButtonBike @$categorySelected="categorySelected" />
        <ButtonHiking @$categorySelected="categorySelected" />
        <ButtonWater @$categorySelected="categorySelected" />
        <ButtonActivities @$categorySelected="categorySelected" />
    </div>
  </div>
</template>

<script>
import Logo from "./nav/Logo.vue";
import ButtonBike from "./nav/ButtonBike.vue";
import ButtonHiking from "./nav/ButtonHiking.vue";
import ButtonWater from "./nav/ButtonWater.vue";
import ButtonActivities from "./nav/ButtonActivities.vue";
export default {
  name: "HollyInfoScreen",
  components: {
    Logo,
    ButtonBike,
    ButtonHiking,
    ButtonWater,
    ButtonActivities
  },
  data: function() {
    return {
        landing: true,
        info: false
    }
  },
  methods: {
    categorySelected: function(id) {
      console.log("in landing: " + id);
      this.$emit("$categorySelected", id);
    }
  }
};
</script>

<style scoped src="./constants/navCSS.css">
</style>

<style>
.lhs-nav {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 2;
  width: 25vw;
  height: 100vh;
  overflow: hidden;
  background: #c7800e;
}
</style>

