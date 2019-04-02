<template>
  <div class="landing">
    <router-link class="logo-link" :to="'/hollyMap'" exact>
        <img class="logo" src="../../assets/holly/logo-final.png">
    </router-link>
  </div>
</template>

<script>
export default {
  name: "HollyLanding",
  components: {}
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
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
}
.logo-link {
  display: flex;
  justify-content: center;
}
.logo {
  width: 50%;
  margin: auto;
  transition: transform 0.2s ease-in-out;
}
.logo:hover {
  transform: scale(1.05);
}
</style>