<template>
  <div class="lhs-nav">
    <Logo />
  </div>
</template>

<script>
import Logo from "./nav/Logo.vue";
export default {
  name: "HollyInfoScreen",
  components: {
    Logo
  }
};
</script>

<style scoped>
.lhs-nav {
  position: absolute;
  left: 0;
  top: 0;
  z-index: 2;
  width: 25vw;
  height: 100vh;
  background: #c7800e;
}
</style>