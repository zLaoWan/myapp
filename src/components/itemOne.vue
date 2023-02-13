<template>
  <div>
    <h2>销售总量</h2>
    <div class="chart" id="oneCharts">图表的容器</div>
  </div>
</template>

<script>
import { inject, onMounted, reactive } from "vue";
export default {
  setup() {
    let $echarts = inject("echarts");
    let $http = inject("axios");

    let data = reactive({});
    let xdata = reactive([]);
    let ydata = reactive([]);

    function setData() {
      xdata = data.data.chartData.chartData.map((value) => value.title);
      ydata = data.data.chartData.chartData.map((value) => value.num);
      console.log("xdata", xdata);
      console.log("ydata", ydata);
    }

    async function getState() {
      data = await $http({ url: "/one/data" });
    }

    onMounted(() => {
      let myCharts = $echarts.init(document.getElementById("oneCharts"));

      // 调用请求
      getState().then(() => {
        setData();

        myCharts.setOption({
          grid: {
            top:"3%",
            left:"1%",
            right:"6%",
            bottom:"3%",
            containLabel:true //包含文字
          },
          xAxis: {
            type: "value",
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            }
          },
          yAxis: {
            type: "category",
            data: xdata,
            axisLine: {
              lineStyle: {
                color: '#fff'
              }
            }
          },
          series: [
            { 
              data: ydata, 
              type: "bar",
              itemStyle:{
                normal: {
                  barBorderRadius:[0,20,20,0],
                  color: new $echarts.graphic.LinearGradient(0,0,1,0, 
[                  {
                    offset:0,
                    color:"#005eaa"
                  },
                  {
                    offset:0.5,
                    color:"#339ca8"
                  },
                  {
                    offset:1,
                    color:"#cda819"
                  },]
                  )
                }
              }
            }
          ],
        });
      });
    });
    return {
      getState,
      data,
      xdata,
      ydata,
      setData,
    };
  },
};
</script>
<style scoped>
h2 {
  height: .6rem;
  color: #fff;
  line-height: .6rem;
  font-size: .25rem;
  text-align: center;
}
.chart {
  height: 4.5rem;
}
</style>

