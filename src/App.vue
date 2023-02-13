<template>
  <router-view/>
</template>

<script>
import {provide} from 'vue'
import * as echarts from 'echarts'
import axios from 'axios'

// 设置基准路径
axios.defaults.baseURL="http://localhost:8888"

export default {
  setup() {
    // provider("另起名称","传递的内容")
    provide("echarts",echarts)
    provide("axios",axios)
  }
}
</script>

<style lang="less">
body { 
  background: url('~@/assets/bg.jpg') top center no-repeat;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>
