<template>
  <div id="app">
    <el-container>
      <el-header><NavBar/></el-header>
      <el-container>
        <el-aside width="200px"><UpLoad/></el-aside>
        <el-container>
          <el-main>
            <CommitBtn/>
            <VedioPlay/>
          </el-main>
          <el-footer>Footer</el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import NavBar from '@/components/NavBar.vue';
import UpLoad from '@/components/UpLoad.vue';
import VedioPlay from '@/components/VedioPlay.vue';
import CommitBtn from '@/components/CommitBtn.vue';
import axios from "axios";

export default {
  name: "App",
  components: {
    NavBar,
    UpLoad,
    VedioPlay,
    CommitBtn,
  },
};
</script>

<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
