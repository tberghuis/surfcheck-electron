<script setup>
import Surfcam from "./components/Surfcam.vue";
import { ref, onMounted, watch } from "vue";

const camUrls = [
  "https://cams.cdn-surfline.com/cdn-au/au-byronbay/playlist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-thepassoverview/playlist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-lennoxhead/playlist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-ballinashellybeach/playlist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-ballinalighthouse/chunklist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-evanshead/playlist.m3u8",
];

const camIndex = ref(0);

const toggleCam = (index) => {
  // camIndex.value++;
  // console.log("camIndex", camIndex.value);
  // camIndex.value = camIndex.value % 2;
};
</script>

<template>
  <div class="cam-list">
    <button @click="camIndex = 0">the wreck</button>
    <button @click="camIndex = 1">the pass</button>
    <button @click="camIndex = 2">lennox</button>
    <button @click="camIndex = 3">shelly</button>
    <button @click="camIndex = 4">northwall</button>
    <button @click="camIndex = 5">evans</button>
  </div>
  <div class="cam-container">
    <Surfcam :camUrl="camUrls[camIndex]" />
  </div>
</template>

<style>
#app {
  display: flex;
  /* max-width: 100vw; */
}

.cam-list {
  display: flex;
  flex-direction: column;
  width: 200px;
  max-width: 200px;
  min-width: 200px;
  /* flex-basis: 2; */
}

.cam-list button {
  width: 100%;
}

.cam-container {
  /* flex-basis: 4; */
}
</style>
