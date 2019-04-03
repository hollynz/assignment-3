<template>
  <router-link class="logo-link" :to="'/hollyMap'" exact>
    <img class="logo" src="../../../assets/holly/logo-final.png">
  </router-link>
</template>

<script>
export default {
    name: "Logo"
};
</script>

<style scoped>
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


</style>
