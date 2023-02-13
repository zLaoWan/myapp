<template>
  <div>
    <header>
      <h1>大数据可视化项目</h1>
    </header>

    <!-- 大容器 -->
    <section class="container">

      <!-- 左容器 -->
      <section class="itemLeft">
        <ItemPage>
          <itemOne></itemOne>
        </ItemPage>
        <ItemPage>
          <itemTwo></itemTwo>
        </ItemPage>
      </section>

      <!-- 中容器 -->
      <section class="itemCenter">
        <mapPage></mapPage>
      </section>

      <!-- 右容器 -->
      <section class="itemRight">
        <ItemPage>
          <itemThree></itemThree>
        </ItemPage>
        <ItemPage>
          <itemFour></itemFour>
        </ItemPage>
      </section>
    </section>
  </div>
</template>

<script>
import ItemPage from "@/components/itemPage.vue";

import itemOne from "@/components/itemOne.vue";
import itemTwo from "@/components/itemTwo.vue";
import itemThree from "@/components/itemThree.vue";
import itemFour from "@/components/itemFour.vue";
import mapPage from "@/components/mapPage.vue";

import {inject} from "vue"
export default {
  components: {
    ItemPage,itemOne,itemTwo,itemThree,itemFour,mapPage
  },

  setup() {
    let $echarts = inject("echarts")
    let $http = inject("axios")
    console.log($echarts)
    console.log($http)
  }
} 
</script>

<style lang="less">
  header {
    height: 1rem;
    width: 100%;
    background-color: rgba(0, 0, 255, 0.2);
    // 标题的文字样式
    h1 {
      font-size: 0.375rem;
      color: #fff;
      text-align: center;
      line-height: 1rem;
    }
  }

  // 大容器样式
  .container {
    // 最大最小的宽度
    min-width: 1024px;
    max-width: 2048px;
    margin: 0 auto;
    padding: .125rem .125rem 0;
    // background-color: gray;
    display: flex;

    // 设置左右在页面的份数
    .itemLeft,
    .itemRight {
      flex:3;
    }
    .itemCenter{
      flex:5;
      height: 10.5rem;
      border: 1px solid blue;
      padding: .625rem;
      margin: .25rem;
    }
  }
</style>