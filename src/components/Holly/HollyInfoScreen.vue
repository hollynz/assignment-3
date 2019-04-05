<template>
  <div class="lhs-nav">
    <Logo @$goHome="goHome" />
    <div :class="{buttonsLanding: this.$parent.$parent.$data.landing, buttonsInfo: this.$parent.$parent.$data.info}">
      <ButtonBike @$categorySelected="categorySelected"/>
      <ButtonHiking @$categorySelected="categorySelected"/>
      <ButtonWater @$categorySelected="categorySelected"/>
      <ButtonActivities @$categorySelected="categorySelected"/>
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
  methods: {
    categorySelected: function(id) {
      this.$emit("$categorySelected", id);
    },
    goHome: function() {
      this.$emit("$goHome");
    }
  }
};
</script>

<style scoped src="./constants/navCSS.css">
</style>

<style scoped>
.lhs-nav {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 2;
  width: 18vw;
  height: 100vh;
  overflow: hidden;
  background: #c7800e;
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  justify-content: center;
}
</style>

