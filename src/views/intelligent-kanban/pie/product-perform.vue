<template>
  <div :id="id" :class="className" :style="{height:height,width:width}">
    <div>
      <el-table :data="tableData" stripe style="width: 100%">
        <el-table-column prop="date" label="Date" width="180" />
        <el-table-column prop="name" label="Name" width="180" />
        <el-table-column prop="address" label="Address" />
      </el-table>
    </div>
  </div>
</template>

<script>
import echarts from 'echarts'
import resize from './mixins/resize'
export default {
  mixins: [resize],
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    id: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '200px'
    },
    height: {
      type: String,
      default: '200px'
    }
  },
  data() {
    return {
      chart: null
    }
  },
  mounted() {
    this.initChart()
  },
  beforeDestroy() {
    if (!this.chart) {
      return
    }
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    initChart() {
      this.chart = echarts.init(document.getElementById(this.id))

      this.chart.setOption({
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b}: {c} ({d}%)'
        },
        legend: {
          orient: 'horizontal',
          data: ['制造成本', '产量', '质量', '安全环保'],
          textStyle: {
            color: 'white'
          }
        },
        series: [
          {
            name: '访问来源',
            type: 'pie',
            selectedMode: 'single',
            radius: ['15%', '30%'],

            label: {
              normal: {
                position: 'inner',
                show: false
              }
            },
            labelLine: {
              normal: {
                show: false
              }
            },
            data: [
              { value: 25.8, name: '制造成本' },
              { value: 77.56, name: '产量' },
              { value: 34.49, name: '质量' },
              { value: 46.22, name: '安全环保' }
            ]
          },
          {
            name: '访问来源',
            type: 'pie',
            selectedMode: 'single',
            radius: ['40%', '55%'],
            label: {
              normal: {
                position: 'inner',
                show: false
              }
            },
            data: [
              { value: 65.41, name: '制造成本' },
              { value: 25.13, name: '产量' },
              { value: 27.67, name: '质量' },
              { value: 50.85, name: '安全环保' }
            ]
          }
        ]
      })
    }
  }
}
</script>
