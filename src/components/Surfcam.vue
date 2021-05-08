<template>
  <div>
    surfcam {{camUrl}}
    <video ref="video" muted="muted"></video>
  </div>
</template>

<script>

// todo use composition api instead of mounted hooks

import Hls from "hls.js";

export default {
  name: "Surfcam",
  props: {
    camUrl: String
  },
  mounted: function() {
    var video = this.$refs.video;

    if (Hls.isSupported()) {
      var hls = new Hls();
      hls.loadSource(this.camUrl);
      hls.attachMedia(video);
      hls.on(Hls.Events.MANIFEST_PARSED, function() {
        video.play();
      });
    }
  }
};
</script>

<style>
</style>