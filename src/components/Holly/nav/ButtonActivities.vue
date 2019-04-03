
<template>
  <router-link :class="{buttonLanding: landing, buttonInfo: info}" :to="'/hollyMap'" exact>
    <img :class="{logoLanding: landing, logoInfo: info}" src="../../../assets/holly/button-activities.png">
  </router-link>
</template>

<script>
export default {
  name: "ButtonActivities",
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
