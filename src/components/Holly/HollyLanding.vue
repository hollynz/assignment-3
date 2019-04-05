<template>
  <div class="landing">
    <!-- <div class="container"> -->
      <Logo />
      <div>
        <h1>What are you keen on?</h1>
      </div>
      <div class="md-form mt-0 search">
        <input class="form-control" type="text" placeholder="Search" aria-label="Search">
      </div>
      <div :class="{buttonsLanding: this.$parent.$parent.$data.landing, buttonsInfo: this.$parent.$parent.$data.info}">
        <ButtonBike @$categorySelected="categorySelected" />
        <ButtonHiking @$categorySelected="categorySelected" />
        <ButtonWater @$categorySelected="categorySelected" />
        <ButtonActivities @$categorySelected="categorySelected" />
      </div>
    <!-- </div> -->
  </div>
</template>

<script>
import Logo from "./nav/Logo.vue";
import ButtonBike from "./nav/ButtonBike.vue";
import ButtonHiking from "./nav/ButtonHiking.vue";
import ButtonWater from "./nav/ButtonWater.vue";
import ButtonActivities from "./nav/ButtonActivities.vue";

export default {
  name: "HollyLanding",
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
    }
  }
};
</script>

<style scoped>
.landing {
  position: absolute;
  z-index: 1000;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
}
</style>

<style scoped src="./constants/navCSS.css">
</style>