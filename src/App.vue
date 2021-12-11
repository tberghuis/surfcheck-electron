<script setup>
import Surfcam from "./components/Surfcam.vue";
import { ref, onMounted, watch } from "vue";
import { cams } from "./cams.js";

const camIndex = ref(26);
</script>

<template>
  <div class="cam-list">
    <button
      v-for="(cam, index) in cams"
      :key="cam.name"
      @click="camIndex = index"
    >
      {{ cam.name }}
    </button>
  </div>
  <div class="cam-container">
    <Surfcam :camUrl="cams[camIndex].url" />
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
