<!-- controls：向用户显示播放按钮控件 -->
<template>
  <video
    ref="video"
    class="video-js vjs-default-skin"
    width="600"
    height="400"
    controls
  >
    <!-- <source :src="this.processedUrl" type="video/mp4" /> -->
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
      options: {
        playbackRates: [0.1, 0.2, 0.5, 1.0], //播放速度
        autoplay: false, //如果true,浏览器准备好时开始播放。
        muted: false, // 默认情况下将会消除任何音频。
        loop: false, // 导致视频一结束就重新开始。
        preload: "auto", // auto浏览器选择最佳行为,立即开始加载视频(如果浏览器支持)
        //language: 'zh-CN',
        aspectRatio: "16:9", // 播放器的比例。用冒号分隔的两个数字(例如"16:9"或"4:3")
        fluid: true, // 当true时，播放器将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        sources: [
          {
            type: "video/mp4",
            src: "", //url地址 http://localhost:8081/video/
          },
        ],
        //poster: '', //你的封面地址
        // width: document.documentElement.clientWidth,
        notSupportedMessage: "此视频暂无法播放，请稍后再试", //无法播放媒体源时显示的默认信息。
        controlBar: {
          timeDivider: true,
          durationDisplay: true,
          remainingTimeDisplay: false,
          fullscreenToggle: true, //全屏按钮
        },
        errorDisplay: false,
        posterImage: false,
        bigPlayButton: false,
        textTrackDisplay: false,
      },
    };
  },
  mounted() {
    // 渲染视频
    this.player = this.$video(this.$refs.video,this.options);
    this.$bus.$on("getProcedUrl", (res) => {
      console.log("VedioPlay组件接受到信息：", res);
      console.log(res.name);
      this.options.sources[0].src = res.ProcessedUrl;
      console.log(this.options.sources[0].src);
    });
  },
  //当视频路径发生变化时, 重新加载视频资源:
  watch: {
    src(){
      console.log("进入watch函数:");
      this.player.src({src:this.src,type:'video/mp4'});
    },
  },

  computed:{
    src(){
      console.log("进入computed函数:");
      return this.options.sources[0].src;
    }
  },

  
};
</script>



