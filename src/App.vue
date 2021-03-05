<template>
  <div id="app">
    <img src="./assets/logo.png" width="70%" alt="" />
    <Pokedex />
  </div>
</template>

<script>
import Pokedex from "./components/Pokedex";

export default {
  name: "App",

  components: {
    Pokedex
  },

  data: () => ({
    //
  })
};
</script>

<style>
body {
  background-color: red;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}

.logo {
  max-width: 70%;
}
</style>
