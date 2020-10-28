``<template>
<div>
    <div id="map"></div>
    <button class="btt" @click="show=!show">Show</button>
    <nav id="menu"></nav>
</div>
</template>

<script>
export default {
    data(){
        return{
            map:null,
            show:true
        }
    },
    mounted() {
    const mapboxgl = require('mapbox-gl')
    this.map = new mapboxgl.Map({
      accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg',
      container: 'map',
      style: 'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8',
      center: [8.531512, 47.380471],
      zoom: 2
       
    })

    this.map.on('load', function() {
        this.map.addSource('pointsrc',{
        type:'geojson',
        data: {
            "type": "FeatureCollection",
            "features": [
                {
                "type": "Feature",
                "properties": {},
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                    78.046875,
                    15.114552871944115
                    ]
                }
                },
                {
                "type": "Feature",
                "properties": {},
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                    87.1875,
                    41.244772343082076
                    ]
                }
                }
            ]
        }
    })
    this.map.addSource('linesrc',{
        type:'geojson',
        data:
            {
            "type": "FeatureCollection",
            "features": [
                {
                "type": "Feature",
                "properties": {},
                "geometry": {
                    "type": "LineString",
                    "coordinates": [
                    [
                        53.78906249999999,
                        59.355596110016315
                    ],
                    [
                        109.3359375,
                        64.16810689799152
                    ]
                    ]
                }
                },
                {
                "type": "Feature",
                "properties": {},
                "geometry": {
                    "type": "LineString",
                    "coordinates": [
                    [
                        93.8671875,
                        56.36525013685606
                    ],
                    [
                        141.328125,
                        62.2679226294176
                    ]
                    ]
                }
                }
            ]
        }
        
    })

    this.map.addLayer({
        id:'points',
        source:'pointsrc',
        type:'circle',
        paint:{
            'circle-radius':10,
            'circle-color':'red'
        }
    })
    })
    },
}

</script>

<style scoped>
#map{
    width:100%;
    height:75vh
}
.btt{
    width:200px;
    margin:20px;
    border:2px solid red;
    cursor:pointer;
}
#menu {
background: #fff;
z-index: 1;
top: 10px;
right: 10px;
border-radius: 3px;
width: 120px;
border: 1px solid rgba(0, 0, 0, 0.4);
font-family: 'Open Sans', sans-serif;
}
 
#menu a {
font-size: 13px;
color: #404040;
display: block;
margin: 0;
padding: 0;
padding: 10px;
text-decoration: none;
border-bottom: 1px solid rgba(0, 0, 0, 0.25);
text-align: center;
}
 
#menu a:last-child {
border: none;
}
 
#menu a:hover {
background-color: #f8f8f8;
color: #404040;
}
 
#menu a.active {
background-color: #3887be;
color: #ffffff;
}

</style>