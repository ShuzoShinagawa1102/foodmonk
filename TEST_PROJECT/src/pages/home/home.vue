<template>
  <!-- サーチバー -->
  <page-searchbar />
  <!-- マップ -->
  <div>
    <google-map :myLatLng="{lat: -25.344, lng: 131.036}" :zoom="4" />
  </div>
  <!-- ナビゲーションバー -->
  <page-navbar :current="0" @clickBarItem = "redirectToByIndex"/>

</template>

<script setup lang="ts">
import { ref } from "vue";
const title = ref("Hello Vue");

const redirectToByIndex = () => {
  alert();
}

</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 290rpx;
  width: 290rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}
</style>
