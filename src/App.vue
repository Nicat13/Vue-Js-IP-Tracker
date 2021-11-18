<template>
  <div id="app">
    <LocationInfo @mapurl="passdata"></LocationInfo>
    <MapLocation :url="url"></MapLocation>
  </div>
</template>

<script>
import LocationInfo from "./components/LocationInfo";
import MapLocation from "./components/MapLocation";

export default {
  name: "App",
  components: {
    LocationInfo,
    MapLocation,
  },
  data() {
    return {
      url: "",
      ismounted: true,
    };
  },
  methods: {
    passdata(url) {
      this.url = url;
    },
  },
};
</script>
<style>
</style>
