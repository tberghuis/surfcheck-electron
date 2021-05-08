<template>
  <div>
    <Surfcam :camUrl="beachData.lennox.streamUrl" />
    <Surfcam :camUrl="beachData.shelly.streamUrl" />
    <Surfcam :camUrl="beachData.ballina.streamUrl" />
  </div>
</template>

<script>
import Surfcam from "./components/Surfcam.vue";

import beachData from "./data/beach-data";

export default {
  name: "App",
  components: {
    Surfcam,
  },

  setup() {
    return {
      beachData,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
