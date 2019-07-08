<template>
  <v-chart theme="ovilia-green" :options="polar" class="chart" />
</template>
<script>
import echarts from "echarts";
import ECharts from "vue-echarts/components/ECharts";
export default {
  components: {
    "v-chart": ECharts
  },
  data() {
    return {
      polar: {
        title: {
          x: "center"
        },
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b} : {c} ({d}%)"
        },
        legend: {
          orient: "horizontal",
          x: "center",
          data: ["制造成本", "质量", "产量", "安全环保"],
          textStyle: {
            color: "white"
          }
        },
        series: [
          {
            name: "访问来源",
            type: "pie",
            selectedMode: "single",
            radius: ["15%", "30%"],

            label: {
              normal: {
                position: "inner",
                show: false
              }
            },
            labelLine: {
              normal: {
                show: false
              }
            },
            data: [
              { value: 25.28, name: "制造成本" },
              { value: 77.56, name: "质量" },
              { value: 34.4, name: "产量" },
              { value: 46.22, name: "安全环保" }
            ]
          },
          {
            name: "访问来源",
            type: "pie",
            radius: ["40%", "55%"],
            label: {
              normal: {
                position: "inner",
                show: false
              }
            },
            data: [
              { value: 65.41, name: "制造成本" },
              { value: 25.13, name: "质量" },
              { value: 27.67, name: "产量" },
              { value: 50.85, name: "安全环保" }
            ]
          }
        ]
      }
    };
  }
};
</script>
<style scoped>
.chart {
  width: 50%;
  height: 70%;
  margin-top: 20px;
}
</style>
