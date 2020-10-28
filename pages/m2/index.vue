<template>
<div>
    <nav id="menu"></nav>
    <div id="map"></div>
</div>
</template>

<script>
export default {
    data(){
        return{
            map:null,
            show:false
        }
    },
    mounted(){
         this.createMap()
    },
    methods:{
        createMap(){
            const mapboxgl = require('mapbox-gl')
            this.map = new mapboxgl.Map({
                accessToken: 'pk.eyJ1IjoiZGFpeWFhbm1hcGJveCIsImEiOiJja2Z3N2I2dzUydmVmMnlzNXFoNWVrZDFnIn0.kzAZEkwT52gW50jJZhyVgg',
                container:'map',
                style:'mapbox://styles/daiyaanmapbox/ckfxn26sp0efl19lgp69obgg8',
                zoom:2,
                center: [8.531512, 47.380471]
            })
         this.map.on('style.load', () => {
            const waiting = () => {
                 if (!this.map.isStyleLoaded()) {
                    setTimeout(waiting, 200);
                }
                else {
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
                        this.map.addLayer({
                            id:'lines',
                            source:'linesrc',
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
                        })
                        var toggleableLayerIds = ['points', 'lines'];
                        // set up the corresponding toggle button for each layer
                        for (var i = 0; i < toggleableLayerIds.length; i++) {
                        var id = toggleableLayerIds[i];
                        
                        var link = document.createElement('a');
                        link.href = '#';
                        link.className = 'active';
                        link.textContent = id;
                        
                        //manually setting layer visibilty as default is 'undefined'
                        this.map.setLayoutProperty("points", 'visibility', 'visible');
                        this.map.setLayoutProperty("lines", 'visibility', 'visible');
                        
                        link.onclick = function (e) {
                        var clickedLayer = this.textContent;
                        e.preventDefault();
                        e.stopPropagation();

                        var visibility = this.map.getLayoutProperty(clickedLayer, 'visibility');
                        
                        // toggle layer visibility by changing the layout object's visibility property
                        if (visibility === 'visible') {
                        this.map.setLayoutProperty(clickedLayer, 'visibility', 'none');
                        this.className = '';
                        } else {
                        this.className = 'active';
                        this.map.setLayoutProperty(clickedLayer, 'visibility', 'visible');
                        }
                        };
                        
                             var layers = document.getElementById('menu');
                            layers.appendChild(link);
                       
                        }      
                        }
                        };
                        waiting();
                        });
                        }
                    },
                }

</script>

<style scoped>
#map{
    width:100%;
    height:75vh
}
#menu {
background:pink;
position: absolute;
z-index: 1;
top: 60px;
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
border-bottom: 1px solid black;
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
 
#menu a.active:hover {
background: #3074a4;
}
</style>