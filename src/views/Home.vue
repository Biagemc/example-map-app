<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style></style>

<script>
const mapboxgl = require("mapbox-gl/dist/mapbox-gl.js");

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  created: function() {
    mapboxgl.accessToken = "pk.";
    var map = new mapboxgl.Map({
      container: "YOUR_CONTAINER_ELEMENT_ID",
      style: "mapbox://styles/mapbox/streets-v11",
    });
  },
  methods: {},
};
</script>
