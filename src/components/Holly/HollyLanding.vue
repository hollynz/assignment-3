<template>
  <div class="landing">
    <div class="container">
      <router-link class="logo-link" :to="'/hollyMap'" exact>
        <img class="logo" src="../../assets/holly/logo-final.png">
      </router-link>
      <div>
        <h1>What are you keen on?</h1>
      </div>
      <div class="md-form mt-0 search">
        <input class="form-control" type="text" placeholder="Search" aria-label="Search">
      </div>
      <div class="buttons">
        <router-link class="button" :to="'/hollyMap'" exact>
          <img class="logo" src="../../assets/holly/dh-icon.png">
        </router-link>
        <router-link class="button" :to="'/hollyMap'" exact>
          <img class="logo" src="../../assets/holly/kayak.png">
        </router-link>
        <router-link class="button" :to="'/hollyMap'" exact>
          <img class="logo" src="../../assets/holly/footprints.png">
        </router-link>
        <router-link class="button" :to="'/hollyMap'" exact>
          <img class="logo" src="../../assets/holly/paragliding.png">
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HollyLanding",
  components: {}
};
</script>

<style scoped>
.landing {
  position: absolute;
  z-index: 1000;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
}
.container {
  /* background: yellow; */
  width: 30%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}
.logo-link {
  width: 100%;
  display: flex;
  justify-content: center;
}
.logo {
  width: 30%;
  margin: auto;
  transition: transform 0.2s ease-in-out;
}
.logo:hover {
  transform: scale(1.05);
}
h1 {
  color: #fff;
}
.search {
  width: 28vw;
}
.search input {
  font-size: 1.8em;
  margin-top: 2%;
  box-shadow: 0px 0px 10px 2px #291E02;
}
.buttons {
  display: flex;
  flex-direction: row;
  width: 35vw;
}
.button {
  display: flex;
  justify-content: center;
}
.button img {
  width: 80%;
  border: transparent solid 6px;
  border-radius: 50%;
}
.button img:hover {
  border: rgba(255, 255, 255, 0.8) solid 6px;
  border-radius: 50%;
}
</style>