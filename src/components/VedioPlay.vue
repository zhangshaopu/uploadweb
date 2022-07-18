<!-- controls：向用户显示播放按钮控件 -->
<template>
  <video 
    ref="video"
    class="video-js vjs-default-skin"
    width="600"
    autoplay="autoplay"
    height="400"
    controls
  >
    <source src="http://localhost:8081/video/pig14" />
  </video>
</template>

<script>
import videojs from "video.js";
import "video.js/dist/video-js.css";
export default {
  name: "VedioPlay",
  data() {
    return {
      player: null, // 用来存储当前 video
    };
  },
  mounted() {
    // 渲染视频
    this.player = this.$video(this.$refs.video);
    this.$bus.$on("getProcedUrl", (res) => {
      console.log("VedioPlay组件接受到信息：", res);
      //this.src = res.src;
      //this.playerOptions.sources.type = res.type;
    });
  },
};
</script>



