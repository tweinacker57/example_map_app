<template>
  <div class="home">
    <div id="map"></div>
    <h1>{{ places }}</h1>
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}
#marker {
  background-image: url("https://docs.mapbox.com/mapbox-gl-js/assets/washington-monument.jpg");
  background-size: cover;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.mapboxgl-popup {
  max-width: 200px;
}
</style>

<script>
export default {
  data: function () {
    return {
      places: [{ lng: -71.25336029235405, lat: 42.07020495062423 }],
    };
  },
  mounted: function () {
    mapboxgl.accessToken = process.env.VUE_APP_MY_API_KEY;
    var house = [-71.25336029235405, 42.07020495062423];
    var map = new mapboxgl.Map({
      container: "map", // container id
      style: "mapbox://styles/mapbox/light-v10", // style URL
      center: house, // starting position [lng, lat]
      zoom: 18, // starting zoom
    });
    var popup = new mapboxgl.Popup({ offset: 25 }).setText(
      "This is the house I grew up in"
    );
    var el = document.createElement("div");
    el.id = "marker";
    new mapboxgl.Marker(el).setLngLat(house).setPopup(popup).addTo(map);
  },
  methods: {},
};
</script>

