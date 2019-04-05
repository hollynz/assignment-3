<template>
    <div class="md-form mt-0" :class="{searchLanding: this.$parent.$parent.$parent.$data.landing, searchInfo: this.$parent.$parent.$parent.$data.info}">
      <input class="form-control" type="text" placeholder="Search" aria-label="Search">
    </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    // categorySelected: function(evt) {
    //   this.$emit("$categorySelected", evt.target.id);
    // }
  }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
