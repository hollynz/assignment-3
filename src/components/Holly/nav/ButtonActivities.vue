
<template>
  <div :class="{buttonLanding: landing, buttonInfo: info}">
    <img @click="categorySelected" id="activities" :class="{logoLanding: landing, logoInfo: info}" src="../../../assets/holly/button-activities.png">
  </div>
</template>

<script>
export default {
  name: "ButtonActivities",
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
