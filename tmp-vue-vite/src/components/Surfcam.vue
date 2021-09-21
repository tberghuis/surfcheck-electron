<template>
  <div>{{ camUrl }}</div>
  <video ref="video" muted="muted"></video>
</template>

<script>
// todo use composition api instead of mounted hooks

import Hls from "hls.js";
import { ref, onMounted, watchEffect } from "vue";

export default {
  name: "Surfcam",
  props: {
    camUrl: String,
  },
  setup(props) {
    const video = ref(null);

    // watch(
    //   () => props.camUrl,
    //   (camUrl) => {
    //     console.log(camUrl, "camUrl");
    //   }
    // );

    // onMounted(() => {
    //   console.log("surfcam mounted");
    //   // should I only use one instance???
    //   var hls = new Hls();
    //   hls.loadSource(props.camUrl);
    //   hls.attachMedia(video.value);
    //   hls.on(Hls.Events.MANIFEST_PARSED, function () {
    //     video.value.play();
    //   });
    // });

    // const camUrl = ref(props.camUrl);

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

// export default {
//   name: "Surfcam",
//   props: {
//     camUrl: String,
//   },
//   mounted: function () {
//     console.log("surfcam mounted");
//     var video = this.$refs.video;

//     if (Hls.isSupported()) {
//       var hls = new Hls();
//       hls.loadSource(this.camUrl);
//       hls.attachMedia(video);
//       hls.on(Hls.Events.MANIFEST_PARSED, function () {
//         video.play();
//       });
//     }
//   },
// };
</script>

<style>
</style>