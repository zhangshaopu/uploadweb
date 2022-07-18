<template>
  <div>
    <el-button class = "process-btn" @click="processSubmit">处理视频</el-button>
  </div>
</template>

<script>
import axios from "axios";
export default {
    name:"CommitBtn",
    data(){
      return{
        originUrl:"",
        fileName:"",
      }
    },

    methods:{
      processSubmit(){ // 点击按钮触发函数
        console.log("正在进行post请求")

        axios.post("http://localhost:8081/process",{
          context:"processing",
          url:this.originUrl,
          fileName:this.fileName,
        }).then(res=>{
          console.log(res);
          console.log("给Vedioplay发送信息:");
          this.$bus.$emit('getProcedUrl',res.data);
        });
      },
    },

    mounted(){//监听Upload组件传来的信息
      this.$bus.$on('getOriginMsg',(originMsg)=>{
        console.log("btn接收到的originMsg:",originMsg);
        this.originUrl = originMsg.url;
        this.fileName = originMsg.name;
        console.log("testurl:",this.originUrl);
        console.log("testname:",this.fileName);
      })
    }
}
</script>

<style>

</style>