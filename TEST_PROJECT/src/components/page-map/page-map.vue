<template>
    <view class="map">
        <image src="/static/map.png">

        </image>
    </view>
</template>

<script async defer
    setup lang="ts"
    src="https://maps.googleapis.com/maps/api/js?key=AIzaSyDDiCLXghb5ALx0FvTuHTw40dO2hn5f3_8&callback=initMap">

    function initMap() {
    var opts = {
        zoom: 15,
        center: new google.maps.LatLng(35.709984,139.810703)
    };
        var map = new google.maps.Map(document.getElementById("map"), opts);
    }
</script>
<style scoped>


</style>
  