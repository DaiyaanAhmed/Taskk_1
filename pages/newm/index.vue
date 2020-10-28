<template>
  <div id="map">
    <button type="button" @click="show = !show">show = {{ show }}</button>
    <MglMap :accessToken="accessToken" :mapStyle="mapStyle" :center="center" :zoom="zoom">
      <MglGeojsonLayer
        v-if="show"
        :sourceId="geoJsonSource.data.id"
        :source="geoJsonSource"
        :layerId="geoJsonLayer.id"
        :layer="geoJsonLayer"
      />

      <MglGeojsonLayer
        v-if="show"
        :sourceId="geoJsonSource2.data.id"
        :source="geoJsonSource2"
        :layerId="geoJsonLayer2.id"
        :layer="geoJsonLayer2"
      />
    </MglMap>
  </div>
</template>

<script>
export default {
  data() {
    return {
      accessToken:
        "pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg", // your access token. Needed if you using Mapbox maps
      show: false,
      mapStyle: 'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8',
      center: [8.531512, 47.380471],
      zoom: 2,
      showPath: true,
      geoJsonSource: {
        type: "geojson",
        data: {
          id: "points",
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Point",
                coordinates: [78.046875,
                    15.114552871944115]
              }
            },
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Point",
                coordinates: [87.1875,
                    41.244772343082076 ]
              }
            }
          ]
        }
      },
      geoJsonSource2: {
        type: "geojson",
        data: {
          id: "points2",
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Point",
                coordinates: [54.4921875,
                63.074865690586634]
              }
            },
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Point",
                coordinates: [100.1953125,
          68.26938680456564]
              }
            }
          ]
        }
      },
      geoJsonLayer: {
        id: "points",
        type: "circle",
        paint: {
          "circle-radius": 6,
          "circle-color": "#ffffff",
          "circle-stroke-width": 2,
          "circle-stroke-color": "#000000"
        }
      },
      geoJsonLayer2: {
        id: "points2",
        type: "circle",
        paint: {
          "circle-radius": 6,
          "circle-color": "#ff0000",
          "circle-stroke-width": 2,
          "circle-stroke-color": "#000000"
        }
      }
    };
  }
};
</script>

<style scoped>
    #map{
    width:100%;
    height:75vh

}
</style>