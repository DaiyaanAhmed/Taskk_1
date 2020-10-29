<template>
<div>
    <div id="map"></div>
    <ul id="nav">
        <li @click="lo"> Points </li>
        <li> Lines </li>
    </ul>
</div>
</template>

<script>
export default {
    data(){
        return{
            map:null,
            show:false,
            pp:true
        }
    },
    beforeCreate(){
        this.pp=true
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
                       
                        if(!this.pp)
                            {
                                this.map.removeLayer('points')
                                this.map.removeLayer('pointsrc')
                            }
                    
                        }
                        };
                        waiting();
                        });
                        },
                    lo(){
                        this.pp=false
                    }
                    },
                }

</script>

<style scoped>
#map{
    width:100%;
    height:75vh
}
#nav{
    list-style-type: disc;
    text-decoration: none;
}

#nav li:hover{
    cursor: pointer;
}

</style>