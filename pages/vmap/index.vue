<template>
  <MglMap :accessToken="accessToken" :mapStyle="mapStyle" />
</template>

<script>

import Mapbox from "mapbox-gl";


export default {

  data() {
    return {
      accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg', 
      mapStyle: 'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8' 
    };
  },

  created() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = Mapbox;
  }
};
</script>