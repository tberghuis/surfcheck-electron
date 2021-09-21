<template>
  <video ref="video" muted="muted"></video>
</template>

<script>
import Hls from "hls.js";
import { ref, onMounted, watchEffect } from "vue";

export default {
  name: "Surfcam",
  props: {
    camUrl: String,
  },
  setup(props) {
    const video = ref(null);
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

    return {
      video,
    };
  },
};
</script>

<style>
video {
  width: 100%;
}
</style>