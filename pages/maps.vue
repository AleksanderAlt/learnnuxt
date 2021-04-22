<template>
  <div>
    <div ref="map" id="map"></div>
    <v-btn @click="goToSchool">Go to school</v-btn>
  </div>
</template>

<script>
  import { Loader } from "@googlemaps/js-api-loader"
export default {
  mounted(){
    const loader = new Loader({
        apiKey: "",
        version: "weekly",
    });
    loader.load().then(() => {
        this.map = new google.maps.Map(this.$refs['map'], {
            center: { lat: -34.397, lng: 150.644 },
            zoom: 8,
        });
    });
  },
  data(){
    return {
      map: null
    }
  },
  methods: {
      goToSchool(){
          this.map.panTo({lat:59.4269337, lng:24.7428724});
          this.map.setZoom(18);
      }
  }
}
</script>
<style scoped>
    #map {
        height: 600px;
    }
</style>