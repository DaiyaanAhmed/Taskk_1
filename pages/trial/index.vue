<template>
    <MglMap
    :access-token="accessToken"
    :map-style.sync="mapStyle"
    @load="onMapLoaded"
  >
      <MglAttributionControl />
      <MglNavigationControl position="top-right" />
      <MglGeolocateControl position="top-right" />
      <MglScaleControl />
      <MglMarker :coordinates="coordinates">
      <MglPopup>
        <VCard>
          <div style="color:blue">Hello, I'm popup!</div>
        </VCard>
      </MglPopup>
      </MglMarker>
      <MglGeojsonLayer
      :sourceId="geoJsonSource.data.id"
      :source="geoJsonSource"
      :layerId="geoJsonSource.data.id"
      :layer="geoJsonlayer"
    />
  </MglMap>
   
</template>

<script>
import 'mapbox-gl/dist/mapbox-gl.css'
import { MglMap, MglNavigationControl, MglAttributionControl,
    MglFullscreenControl,
    MglScaleControl,MglPopup, MglGeojsonLayer,
    MglMarker, MglGeolocateControl } from "v-mapbox";

export default {
  components: {
    MglMap,
    MglNavigationControl,
    MglGeolocateControl,
    MglMarker,
    MglPopup,
    MglGeojsonLayer
   
  },
  data() {
    return {
      accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg', // your access token. Needed if you using Mapbox maps
      mapStyle: 'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8', // your map style
      coordinates: [2.347297668457031,
          48.854776323867306],
       // geoJsonSource: { 'type': 'geojson', 'data': { 'id': 'pointsrc', 'type': 'Feature', 'properties': {}, 'geometry': { 'type': 'Point', 'coordinates': [2.3009490966796875,48.83082561964199]}}},
        geoJsonSource: {
        type: 'geojson',
        data: {
          id: "pointsrc",
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              geometry: {
                type: "Point",
                coordinates: [2.3009490966796875,48.83082561964199]
              },
              properties: {}
            }
          ]
        },
      },
      geoJsonLayer: {
        type: "circle",
        paint: {
          "circle-color": "red"
        }
      }
    }
  },
    created() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = null;
  },
  methods: {
    onMapLoaded(event) {
      // in component
      this.map = event.map;
    },
  }

  // setup() {
  //   // We need to set mapbox-gl library here in order to use it in template
  //   this.mapbox = Mapbox;
  // }
}
</script>

<style>
.mapboxgl-map{
  height:100vh !important;
}
</style>