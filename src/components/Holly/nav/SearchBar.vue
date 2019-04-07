<template>
<!-- @submit.prevent="addArticle" -->
<!-- <div class="form md-form mt-0" > -->
    <!-- <div class="form-inline">
      <input class="form-control form-control-sm mr-3 w-75" type="text" placeholder="Search" aria-label="Search">
      <i type="submit" class="fas fa-search"></i>
    </div>
    </div> -->
    <div class="input-group md-form form-sm form-2 pl-0" :class="{searchLanding: this.$parent.$parent.$parent.$data.landing, searchInfo: this.$parent.$parent.$parent.$data.info}">
  <input class="form-control my-0 py-1 amber-border" type="text" placeholder="Search" aria-label="Search">
  <div class="input-group-append">
    <span class="input-group-text amber lighten-3" id="basic-text1"><i class="fas fa-search text-grey"
        aria-hidden="true"></i></span>
  </div>
</div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {

    // categorySelected: function(evt) {
    //   this.$emit("$categorySelected", evt.target.id);
    // }

    // <div class="form-group">
    //     <label for="authorInput">Author</label>
    //     <input
    //       type="author"
    //       class="form-control"
    //       id="authorInput"
    //       aria-describedby="authorHelp"
    //       placeholder="Holly Johnson"
    //       ref="author"
    //     />
    //   </div>
    //   <button type="submit" class="btn btn-primary">Submit</button>
  }
};
</script>

<style scoped src="../constants/navCSS.css">
</style>
