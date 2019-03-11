<template>
  <div class="home">
    <PhotoMap
        id="map"
        v-bind:center="{'lat': 65.022690, 'lng': 35.708120}"
        v-bind:location="12"
        v-bind:zoom="16"/>
  </div>
</template>

<script>
// @ is an alias to /src
import PhotoMap from '@/components/PhotoMap.vue'

export default {
  name: 'home',
  components: {
    PhotoMap
  }
}
</script>
<style>
  #map {
    height: 80vh !important;
    width: calc(100% + 20px) !important;
    margin: -10px !important;
  }
</style>
