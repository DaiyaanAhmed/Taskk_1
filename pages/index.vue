<template>
  <div id="map">
    <MglMap :accessToken="accessToken" :mapStyle="mapStyle" :center="center" :zoom="zoom">
      <MglAttributionControl />
      <MglNavigationControl position="top-right" />
      <MglGeolocateControl position="top-right" />
      <MglScaleControl />
      <MglGeojsonLayer
        v-if="pshow"
        :sourceId="geoJsonSource.data.id"
        :source="geoJsonSource"
        :layerId="geoJsonLayer.id"
        :layer="geoJsonLayer"
      />

      <MglGeojsonLayer
        v-if="lshow"
        :sourceId="geoJsonSource2.data.id"
        :source="geoJsonSource2"
        :layerId="geoJsonLayer2.id"
        :layer="geoJsonLayer2"
      />
    </MglMap>
    <div class="tog">
      <h4 style="font-weight:bold"> Click to toggle </h4>
    <input type=checkbox @click="pshow=!pshow" id="pswitch" name="Points"> Points <br>
    <input type=checkbox @click="lshow=!lshow" id="pswitch" name="Lines"> Lines <br>
    </div>
  </div>
</template>

<script>
import { MglMap, MglGeojsonLayer, MglNavigationControl, MglAttributionControl,
    MglFullscreenControl, MglGeolocateControl  } from "v-mapbox";

export default {
  components: {
    MglMap,
    MglGeojsonLayer,
    MglNavigationControl,
    MglGeolocateControl,
  },
  data() {
    return {
      accessToken: process.env.mapToken, // your access token. Needed if you using Mapbox maps
      pshow: false,
      lshow: false,
      mapStyle: "mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8", // your map style
      center: [78.046875,20.138470312451155],
      zoom: 3,
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
                coordinates: [83.671875,32.24997445586331]
              }
            },
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "Point",
                coordinates: [77.16796875,37.579412513438385]
              }
            }
          ]
        }
      },
      geoJsonSource2: {
        type: "geojson",
        data: {
          id: "lines",
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "LineString",
                coordinates: [
                        [
                            73.7841796875,
                            22.836945920943855
                         ],
                        [
                            79.0576171875,
                            16.551961721972525
                        ]
                ]
              }
            },
            {
              type: "Feature",
              properties: {},
              geometry: {
                type: "LineString",
                coordinates: [      
                            [
                                73.4326171875,
                                26.15543796871355
                            ],
                            [
                                85.341796875,
                                21.657428197370653
                            ]
                        ]
              }
            }
          ]
        }
      },
      geoJsonLayer: {
        id: "points",
        type: "circle",
        paint: {
          "circle-radius": 10,
          "circle-color": "red",
          "circle-stroke-width": 2,
          "circle-stroke-color": "#000000"
        }
      },
      geoJsonLayer2: {
        id: "lines",
       type:'line',
      'layout': {
                  'line-cap': 'round',
                  'line-join': 'round',
                },
      'paint': {
                 'line-color': 'red',
                 'line-width': 5,
                 'line-opacity': 0.8
               }
      }
    };
  },
  methods:{
      setup() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = Mapbox;
  }
  },
};
</script>

<style>
.mapboxgl-map{
  height:75vh !important;
}
.tog{
  width:200px;
  margin:20px 40px;
  border: 2px solid navy;
  padding:0px 15px 10px 15px;;
  border-radius:5px;
}
</style>