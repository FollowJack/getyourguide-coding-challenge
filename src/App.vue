<template>
  <div id="app">
    <TourSearch />
  </div>
</template>

<script>
import TourSearch from "./views/TourSearch.vue";

export default {
  name: "app",
  components: {
    TourSearch
  }
};
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
