<template>
  <transition name="home" mode="out-in">
    <div class="background">
      <div class="my-container">
        <div class="row">
          <div class="col-md-6 col-sm-12">
            <router-link :to="'/geoff'">GEOFF</router-link>
          </div>
          <div class="col-md-6 col-sm-12">
            <router-link :to="'/holly'">HOLLY</router-link>
          </div>
          <div class="col-md-6 col-sm-12">
            <router-link :to="'/jack'">JACK</router-link>
          </div>
          <div class="col-md-6 col-sm-12">
            <router-link :to="'/jeremy'">JEREMY</router-link>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Home",
  components: {}
};
</script>

<style scoped>
.background {
  width: 100vw;
  height: 100vh;
}
.my-container {
  height: 100%;
  text-align: center;
}
.home-enter-active,
.home-leave-active {
  transition: opacity 1.5s ease-in-out, transform 0.8s ease-in-out;
}
.home-enter,
.home-leave-to {
  opacity: 0;
}
</style>