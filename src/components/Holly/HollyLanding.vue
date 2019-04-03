<template>
  <div class="landing">
    <div class="container">
      <Logo />
      <div>
        <h1>What are you keen on?</h1>
      </div>
      <div class="md-form mt-0 search">
        <input class="form-control" type="text" placeholder="Search" aria-label="Search">
      </div>
      <div :class="{buttonLanding: landing, buttonInfo: info}">
        <ButtonBike />
        <ButtonHiking />
        <ButtonWater />
        <ButtonActivities />
      </div>
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
  name: "HollyLanding",
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
  }
};
</script>

<style scoped src="./constants/navCSS.css">
</style>

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
.container {
  width: 30%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
h1 {
  color: #fff;
}
.search {
  width: 28vw;
}
.search input {
  font-size: 1.8em;
  margin-top: 2%;
  box-shadow: 0px 0px 10px 2px #291E02;
}
</style>