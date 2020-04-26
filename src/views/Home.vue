<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div id="map-box">
      <div id="menu">
        <input id="streets-v11" type="radio" name="rtoggle" value="streets" checked="checked" />
        <label for="streets">streets</label>
        <input id="light-v10" type="radio" name="rtoggle" value="light" />
        <label for="light">light</label>
        <input id="dark-v10" type="radio" name="rtoggle" value="dark" />
        <label for="dark">dark</label>
        <input id="outdoors-v11" type="radio" name="rtoggle" value="outdoors" />
        <label for="outdoors">outdoors</label>
        <input id="satellite-v9" type="radio" name="rtoggle" value="satellite" />
        <label for="satellite">satellite</label>
      </div>
    </div>
  </div>
</template>

<style>
#map-box {
  position: absolute;
  top: 250px;
  left: 350px;
  width: 50%;
  height: 50%;
}
#menu {
  position: absolute;
  background: #fff;
  padding: 10px;
  font-family: "Open Sans", sans-serif;
}
</style>

<script>
const mapboxgl = require("mapbox-gl/dist/mapbox-gl.js");

export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  mounted: function() {
    mapboxgl.accessToken = "pk.";
    var map = new mapboxgl.Map({
      container: "map-box",
      style: "mapbox://styles/mapbox/streets-v11",
      center: [-74.5, 40], // starting position
      zoom: 9, // starting zoom
    });
    map.addControl(new mapboxgl.NavigationControl());
    var layerList = document.getElementById("menu");
    var inputs = layerList.getElementsByTagName("input");

    function switchLayer(layer) {
      var layerId = layer.target.id;
      map.setStyle("mapbox://styles/mapbox/" + layerId);
    }

    for (var i = 0; i < inputs.length; i++) {
      inputs[i].onclick = switchLayer;
    }
  },
  methods: {},
};
</script>
