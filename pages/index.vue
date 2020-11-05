<template>
  <MglMap :accessToken="accessToken" :mapStyle="mapStyle" />
</template>

<script>
import 'mapbox-gl/dist/mapbox-gl.css'
import Mapbox from "mapbox-gl";
import { MglMap } from "v-mapbox";

export default {
  components: {
    MglMap
  },
  data() {
    return {
      accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg', // your access token. Needed if you using Mapbox maps
      mapStyle: 'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8' // your map style
    };
  },

  setup() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = Mapbox;
  }
};
</script>

<style scoped>
.mapboxgl-map{
  height:100vh !important;
}
</style>