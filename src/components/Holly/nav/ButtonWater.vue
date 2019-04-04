
<template>
  <div :class="{buttonLanding: this.$parent.$parent.$parent.$data.landing, buttonInfo: this.$parent.$parent.$parent.$data.info}">
    <img @click="categorySelected" id="2" :class="{logoLanding: this.$parent.$parent.$parent.$data.landing, logoInfo: this.$parent.$parent.$parent.$data.info}" src="../../../assets/holly/button-water.png">
  </div>
</template>

<script>
export default {
  name: "ButtonWater",
  methods: {
    categorySelected: function(evt) {
      this.$emit("$categorySelected", evt.target.id);
    }
  }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
