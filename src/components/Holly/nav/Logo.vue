<template>
  <router-link :class="{logoLinkLanding: landing, logoLinkInfo: info}" :to="'/hollyMap'" exact>
    <img :class="{logoLanding: landing, logoInfo: info}" src="../../../assets/holly/logo-final.png">
  </router-link>
</template>

<script>
export default {
    name: "Logo",
    data: function() {
      return {
        landing: true,
        info: false
      }
    }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
