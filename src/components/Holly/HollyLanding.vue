<template>
  <div class="landing">
    <Logo @$goHome="goHome"/>
    <div>
      <h1>Choose your destiny:</h1>
    </div>
    <SearchBar/>
    <div
      :class="{buttonsLanding: this.$parent.$parent.$data.landing, buttonsInfo: this.$parent.$parent.$data.info}"
    >
      <ButtonBike @$categorySelected="categorySelected"/>
      <ButtonHiking @$categorySelected="categorySelected"/>
      <ButtonWater @$categorySelected="categorySelected"/>
      <ButtonActivities @$categorySelected="categorySelected"/>
    </div>
  </div>
</template>

<script>
import Logo from "./nav/Logo.vue";
import SearchBar from "./nav/SearchBar.vue";
import ButtonBike from "./nav/ButtonBike.vue";
import ButtonHiking from "./nav/ButtonHiking.vue";
import ButtonWater from "./nav/ButtonWater.vue";
import ButtonActivities from "./nav/ButtonActivities.vue";

export default {
  name: "HollyLanding",
  components: {
    Logo,
    SearchBar,
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
      location.reload();
      this.$emit('$goHome');
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