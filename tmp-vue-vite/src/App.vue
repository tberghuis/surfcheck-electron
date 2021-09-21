<script setup>
import Surfcam from "./components/Surfcam.vue";
import { ref, onMounted, watch } from "vue";

const camUrls = [
  "https://cams.cdn-surfline.com/cdn-au/au-lennoxhead/playlist.m3u8",
  "https://cams.cdn-surfline.com/cdn-au/au-ballinalighthouse/chunklist.m3u8",
];

const camIndex = ref(0);

const toggleCam = () => {
  camIndex.value++;
  console.log("camIndex", camIndex.value);
  camIndex.value = camIndex.value % 2;
};
</script>

<template>
  <div>hello</div>
  <button @click="toggleCam">toggle cam</button>
  <Surfcam :camUrl="camUrls[camIndex]" />
</template>

<style>
#app {
}
</style>
