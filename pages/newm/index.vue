<template>
<div id="map">
  <MglMap :accessToken="accessToken" :mapStyle="mapStyle"/>
</div>
</template>
<script>
import Mapbox from "mapbox-gl";
import { MglMap } from "v-mapbox";
export default {
  components: {
    MglMap
  },
  data() {
    return {
      accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg',// your access token. Needed if you using Mapbox maps
      mapStyle: 'mapbox://styles/mapbox/streets-v11',
      show:false // your map style
    };
  },
  created() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = Mapbox;

  },
  mounted(){
    // this.show=true
  },
  methods:{
  //  setMap(​​​​​map​​​​​) {​​​​​
  // // on load method gives map instance that can be used later
  //  this.mapbox = map
  //   }​​​​​,

  }
};
</script>

<style scoped>
  #map {
        width: 100%;
        height: 200px
    }
</style>