
<template>
  <div
    :class="{buttonLanding: this.$parent.$parent.$parent.$data.landing, buttonInfo: this.$parent.$parent.$parent.$data.info}"
  >
    <img
      @click="categorySelected"
      id="2"
      :class="{buttonImgLanding: this.$parent.$parent.$parent.$data.landing, buttonImgInfo: this.$parent.$parent.$parent.$data.info,
              buttonImgIsActive: buttonImgIsActive}"
      src="../../../assets/holly/button-water.png"
    >
    <p class="buttonTitle">WATER</p>
  </div>
</template>

<script>
export default {
  name: "ButtonWater",
  props: { 
    buttonImgIsActive: false
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
