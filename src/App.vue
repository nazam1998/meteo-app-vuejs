<template>
  <div id="app">
    <Meteo />
  </div>
</template>

<script>
import Meteo from "./components/Meteo.vue";

export default {
  name: "App",
  components: {
    Meteo,
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";
</style>
