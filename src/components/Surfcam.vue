<template>
  <video ref="video" muted="muted"></video>
  <div v-if="render404">404 {{ camUrl }}</div>
</template>

<script>
import Hls from "hls.js";
import { ref, onMounted, watchEffect } from "vue";
import axios from "axios";

export default {
  name: "Surfcam",
  props: {
    camUrl: String,
  },
  setup(props) {
    const video = ref(null);
    const render404 = ref(false);
    watchEffect(() => {
      if (video.value === null) {
        return;
      }

      console.log("camUrl", props.camUrl);
      console.log("video", video.value);
      // should I only use one instance???
      var hls = new Hls();
      hls.on(Hls.Events.MANIFEST_PARSED, function () {
        video.value.play();
      });
      hls.loadSource(props.camUrl);
      hls.attachMedia(video.value);
    });

    watchEffect(async () => {
      console.log("props.camUrl", props.camUrl);
      render404.value = !(await checkHLSActive(props.camUrl));
    });

    return {
      video,
      render404,
    };
  },
};

async function checkHLSActive(url) {
  try {
    let res = await axios.head(url);
    console.log("checkHLSActive", res.status);
    return /2\d\d/.test("" + res.status);
  } catch (err) {
    console.log("checkHLSActive err", url, err);
    return false;
  }
}
</script>

<style>
video {
  width: 100%;
}
</style>