
<template>
  <div :class="{buttonLanding: landing, buttonInfo: info}">
    <img @click="categorySelected" id="water" :class="{logoLanding: landing, logoInfo: info}" src="../../../assets/holly/button-water.png">
  </div>
</template>

<script>
export default {
  name: "ButtonWater",
  data: function() {
    return {
      landing: true,
        info: false
    }
  },
  methods: {
    categorySelected: function(evt) {
      this.$emit("$categorySelected", evt.target.id);
    }
  }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
