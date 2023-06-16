<!-- <template>
  <div>
   <div ref="map" 
    style="height:100vh;width:100vh;">
  
  </div>
  </div>

</template> -->
<!-- AIzaSyDDiCLXghb5ALx0FvTuHTw40dO2hn5f3_8 -->

<script>

export default {
  props: {
    myLatLng: {
      type: Object,
      required: true,
    },
    zoom: {
      type: Number,
      required: true,
    },
  },
  mounted() {
    if (!window.mapLoadStarted) {
      window.mapLoadStarted = true;
      let script = document.createElement('script');
      script.src =
        'https://maps.googleapis.com/maps/api/js?key=AIzaSyDDiCLXghb5ALx0FvTuHTw40dO2hn5f3_8&callback=initMap';
      script.async = true;
      document.head.appendChild(script);
    }
    window.initMap = () => {
      window.mapLoaded = true;
    };

    let timer = setInterval(() => {
      if (window.mapLoaded) {
        clearInterval(timer);
        const map = new window.google.maps.Map(this.$refs.map, {
          center: this.myLatLng,
          zoom: 4,
        });
        new window.google.maps.Marker({ position: this.myLatLng, map });
      }
    }, 500);
  },
};    

</script>