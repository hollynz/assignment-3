
<template>
  <div
    :class="{buttonLanding: this.$parent.$parent.$parent.$data.landing, buttonInfo: this.$parent.$parent.$parent.$data.info}"
  >
    <img
      @click="categorySelected"
      id="1"
      :class="{buttonImgLanding: this.$parent.$parent.$parent.$data.landing, buttonImgInfo: this.$parent.$parent.$parent.$data.info,
              buttonImgIsActive: buttonImgIsActive}"
      src="../../../assets/holly/button-hiking.png"
    >
    <p class="buttonTitle">HIKING</p>
  </div>
</template>

<script>
export default {
  name: "ButtonHiking",
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
