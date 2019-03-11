<template lang="html">
  <v-map  id="mapid" :zoom="zoom" :center="center">
    <v-icondefault></v-icondefault>
    <v-tilelayer
      ref="tileLayer"
      url="url" :attribution="attribution"/>
    <v-marker-cluster>
      <template v-for="instance in testArray">
        <LRotMarker
        :lat-lng="{'lat': instance.latitude, 'lng': instance.longitude}"
          :rotationAngle="instance.azimuth">
          <v-popup>
            <div>
              <img v-bind:src="instance.img_url">
              <div class="photo-title">
                {{instance.title}}
              </div>
            </div>
          </v-popup>
        </LRotMarker>
      </template>
    </v-marker-cluster>
  </v-map>
</template>

<script>
  import * as Vue2Leaflet from 'vue2-leaflet'
  import { latLng, Icon, icon } from 'leaflet'
  // next line is different from the example.vue
  // in example.vue we have:
//import Vue2LeafletMarkercluster from './Vue2LeafletMarkercluster'
  import Vue2LeafletMarkercluster from 'vue2-leaflet-markercluster'
  import iconUrl from 'leaflet/dist/images/marker-icon.png'
  import shadowUrl from 'leaflet/dist/images/marker-shadow.png'
  import Vue2LeafletRotatedMarker from 'vue2-leaflet-rotatedmarker'

  export default {
    components: {
      'v-map': Vue2Leaflet.LMap,
      'v-tilelayer': Vue2Leaflet.LTileLayer,
      'v-icondefault': Vue2Leaflet.LIconDefault,
      'v-popup': Vue2Leaflet.LPopup,
      'v-marker-cluster': Vue2LeafletMarkercluster,
      'LRotMarker': Vue2LeafletRotatedMarker,
    },

  data: function() {
    return {
      testArray: [
        {"id":224,"img_url":"http://www.prokudin-gorsky.org/img/224.jpg","is_liked":false,"content_type":"photo","likes_amount":0,"title":"Троицкий собор. Вид сбоку","number_in_album":174,"longitude":35.7093,"latitude":65.02453,"azimuth":90,"location":12},{"id":226,"img_url":"http://www.prokudin-gorsky.org/img/226.jpg","is_liked":false,"content_type":"photo","likes_amount":0,"title":"Вход в Троицкий собор в Соловецком монастыре","number_in_album":168,"longitude":35.70745,"latitude":65.02436,"azimuth":90,"location":12},{"id":793,"img_url":"http://www.prokudin-gorsky.org/img/793.jpg","is_liked":false,"content_type":"photo","likes_amount":0,"title":"Соловецкий монастырь с озера","number_in_album":171,"longitude":35.7128,"latitude":65.02655,"azimuth":240,"location":12},{"id":1612,"img_url":"http://www.prokudin-gorsky.org/img/1612.jpg","is_liked":false,"content_type":"photo","likes_amount":0,"title":"Вид на монастырь из гостиницы","number_in_album":162,"longitude":35.707,"latitude":65.02575,"azimuth":160,"location":12},{"id":225,"img_url":"http://www.prokudin-gorsky.org/img/225.jpg","is_liked":false,"content_type":"photo","likes_amount":0,"title":"Троицкий собор и электростанция. Вид сбоку. В Соловецком монастыре","number_in_album":173,"longitude":35.70812,"latitude":65.02269,"azimuth":45,"location":12}
      ],
      url:'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
      attribution:'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, ' +
        '<a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
        'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
      lat: 65.022690,
      long: 35.708120,
      clusterOptions: {},
    }
  },
  props: {
    location: Number,
    center: {},
    zoom: Number,
  },


}
</script>

<style lang="css" scoped>
  @import "~leaflet/dist/leaflet.css";
  @import "~leaflet.markercluster/dist/MarkerCluster.css";
  @import "~leaflet.markercluster/dist/MarkerCluster.Default.css";
  img {
    border-radius: 12px 12px 0 0;
    width: 100%;
  }
  .photo-title {
    margin: 0 3%;
  }
  .map-scroll:before {
    content: 'Use ctrl + scroll to zoom the map';
    position: absolute;
    top: 50%;
    left: 50%;
    z-index: 999;
    font-size: 34px;
 }
 .map-scroll:after {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    content: '';
    background: #00000061;
    z-index: 999;
}
</style>
