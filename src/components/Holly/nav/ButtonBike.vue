
<template>
  <div :class="{buttonLanding: this.$parent.$parent.$parent.$data.landing, buttonInfo: this.$parent.$parent.$parent.$data.info}">
    <img @click="categorySelected" id="0" :class="{logoLanding: this.$parent.$parent.$parent.$data.landing, logoInfo: this.$parent.$parent.$parent.$data.info}" src="../../../assets/holly/button-bike.png">
    <p>MOUNTAIN BIKING</p>
  </div>
</template>

<script>
export default {
  name: "ButtonBike",
  methods: {
    categorySelected: function(evt) {
      this.$emit("$categorySelected", evt.target.id);
    }
  }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
