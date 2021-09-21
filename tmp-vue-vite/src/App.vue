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
  <div>
    <div>hello</div>
    <button @click="toggleCam">toggle cam</button>
  </div>
  <div>
    <Surfcam :camUrl="camUrls[camIndex]" />
  </div>
</template>

<style>
#app {
  display: flex;
  /* max-width: 100vw; */
}

</style>
