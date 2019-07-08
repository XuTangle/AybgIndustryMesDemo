<!-- 线性图表 -->
<template>
  <div :id="id" class="chart" :style="{height:chartHeight,width:chartWidth}"></div>
</template>

<script>
import echarts from "echarts";
export default {
  name: "line-chart",
  components: {},
  data() {
    return {
      id: this.generatorOnlyId(),
      chartHeight: "85%",
      chartWidth: "100%"
    };
  },
  props: {
    chartType: {
      type: String,
      default() {
        // 图表类型 line/bar/bar1（x与y轴互换柱图）/pie/pie1(环形图)
        return "bar";
      }
    },
    xText: {
      type: String,
      default() {
        // 横轴文本
        return "x-text";
      }
    },
    yText: {
      type: Array,
      default() {
        // 纵轴文本
        return [];
      }
    },
    xList: {
      type: Array,
      default() {
        // 横轴数据
        return [];
      }
    },
    yList: {
      type: Array,
      default() {
        // 纵轴数据
        return [];
      }
    },
    width: {
      type: Number,
      default: 0
    },
    height: {
      type: Number,
      default: 0
    },
    stackFlag: {
      type: Boolean,
      default() {
        // 横轴文本
        return false;
      }
    }
  },
  computed: {
    legendData() { 
      if (this.chartType == 'pie1' || this.chartType == 'pie') {
        return this.xList.map(function(item) {
          return item[0];
        });
      } else {
        return this.yText.map(function(item) {
          return item[0];
        });
      }
    },
    colorData() {
      return this.xList.map(function(item) {
        return item[1];
      });
    }
  },
  methods: {
    getPositon(point, params, dom, rect, size) {
      var tipHeight = point[1] + size.contentSize[1]; // contentSize: 提示dom 窗口大小
        if(tipHeight > size.viewSize[1] ){              // viewSize: echarts 容器大小
            return [point[0]+40, point[1]-size.contentSize[1]];
        } else if(point[1] < size.contentSize[1]){
            return [point[0]+40, point[1]+20];
        } else {
            return point;
        }
    },
    // 生成图表的唯一ID
    generatorOnlyId() {
      return (
        Date.now() +
        Math.floor(Math.random() * 10000)
      );
    },
    // 生成渲染图表div的宽度与高度
    generatorWithAndHeight() {
      this.chartWidth = `${
        this.width ? this.width : document.body.offsetWidth* this.chartWidth * 0.6
      }px`;
      this.chartHeight = `${
        this.height ? this.height : document.body.offsetHeight* this.chartHeight * 0.6
      }px`;
    },
    // 绘制图表
    drawChart() {
      let chart = echarts.init(document.getElementById(this.id));
      if (chart == undefined) {
        console.error(`echarts init dom id ${this.id} failed`);
        return;
      }
      switch (this.chartType) {
        case "line":
          debugger
          chart.setOption(this.generatorLineOption());
          this.lineSetOptionFun(chart);
          break;
        case "bar":   // 标注柱形图
          chart.setOption(this.generatorBarOption());
          this.barSetOptionFun(chart);
          break;
        case "bar1":  // X Y轴位置互换后的柱形图
          chart.setOption(this.generatorBar1Option());
          this.barSetOptionFun(chart);
        break;
        case "pie":  // 标注饼图
          chart.setOption(this.generatorPieOption());
          this.pieSetOptionFun(chart);
          break;
        case "pie1":  // 环形图
          debugger
          chart.setOption(this.generatorPieOption());
          this.pie1SetOptionFun(chart);
          break;
        default:
          console.error(`chartType ${this.chartType} is invalid`);
          break;
      }
      let self = this;
      let work = null;
      window.addEventListener("resize", function() {
        self.generatorWithAndHeight();
        if (work == null) {
          work = setTimeout(function() {
            chart.resize();
            work = null;
          }, 100);
        }
      });
    },
    lineSetOptionFun(charts) {
      debugger;
      var series = [];
      let yColor = this.yText.map(function(item) {
        return item[1];
      });

      if(this.yList[0].length == 1) {
        let dataList = this.yList.map(function(item) {
          return item[0];
        });
        let serie = {
          name: this.legendData[0],
          type: 'line',
          // 普通样式。
          itemStyle: {
              // 点的颜色。
              color: yColor[0]
          },
          data: dataList
        }
        series.push(serie);
        charts.setOption({
          series: series
        });
        return
      }
    
      for (var i=0;i<this.yList.length;i++){
        let serie = {
          name: this.legendData[i],
          type: 'line',
          stack:this.stackFlag,
          // 普通样式。
          itemStyle: {
              // 点的颜色。
              color: yColor[i]
          },
          data: this.yList[i]
        }
        series.push(serie);
      }
      
      charts.setOption({
        series: series
      });
    },
    generatorLineOption() {
      return {
        title: {
          text: this.titleText,
          subtext: this.subText,
          x: "center"
        },
        legend: {
         x: 'center',
          data:this.legendData,
          itemWidth: 10,
          itemHeight: 8,
          textStyle: {
            color: '#FFF',
            fontSize: 10
          }
        },
        grid: {
          left: "3%",
          right: "4%",
          top: "20%",
          bottom: "5%",
          containLabel: true
        },
        xAxis: {
          type: "category",
          data: this.xList,
          axisTick: {
            alignWithLabel: true
          },
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        yAxis: {
          type: "value",
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        series: []
      };
    },
    barSetOptionFun(charts) {
      debugger
      var series = [];
      let yType = this.yText.map(function(item) {
        return item[1];
      });

      let yColor = this.yText.map(function(item) {
        return item[2];
      });

      if(this.yList[0].length == 1) {
        let dataList = this.yList.map(function(item) {
          return item[0];
        });
        let serie = {
          name: this.legendData[0],
          type: yType[0],
          barWidth: "15%",
          // 普通样式。
          itemStyle: {
              // 点的颜色。
              color: yColor[0]
          },
          data: dataList
        }
        series.push(serie);
        charts.setOption({
          series: series
        });
        return
      }
    
      for (var i=0;i<this.yList.length;i++){
        let serie = {
          name: this.legendData[i],
          type: yType[i],
          barWidth: "15%",
          stack:this.stackFlag,
          // 普通样式。
          itemStyle: {
              // 点的颜色。
              color: yColor[i]
          },
          data: this.yList[i]
        }
        series.push(serie);
      }
      
      charts.setOption({
        series: series
      });
    },
    generatorBarOption() {
      return {
        title: {
          text: this.titleText,
          subtext: this.subText,
          x: "center"
        },
        color: ["#3398DB"],
        tooltip: {
          trigger: "axis",
          axisPointer: {
            // 坐标轴指示器，坐标轴触发有效
            type: "shadow" // 默认为直线，可选为：'line' | 'shadow'
          }
        },
         legend: {
          x: 'center',
          data: this.legendData,
          itemWidth: 10,
          itemHeight: 8,
          textStyle: {
            color: '#FFF',
            fontSize: 10
          }
        },
        grid: {
          left: "3%",
          right: "4%",
          top: "20%",
          bottom: "5%",
          containLabel: true
        },
        xAxis: {
          type: "category",
          data: this.xList,
          axisTick: {
            alignWithLabel: true
          },
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        yAxis: {
          type: "value",
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        series: []
      };
    },
    generatorBar1Option() {
      return {
        title: {
          text: this.titleText,
          subtext: this.subText,
          x: "center"
        },
        color: ["#3398DB"],
        tooltip: {
          trigger: "axis",
          axisPointer: {
            // 坐标轴指示器，坐标轴触发有效
            type: "shadow" // 默认为直线，可选为：'line' | 'shadow'
          },
          position: function(point, params, dom, rect, size){ // point: 鼠标位置
            return this.getPositon(point, params, dom, rect, size);    
          }
        },
        legend: {
          x: 'center',
          data:this.legendData,
          itemWidth: 10,
          itemHeight: 8,
          textStyle: {
            color: '#FFF',
            fontSize: 10
          }
        },
        grid: {
          left: "3%",
          right: "4%",
          top: "20%",
          bottom: "5%",
          containLabel: true
        },
        xAxis:  {
          type: "value",
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        yAxis: {
          type: "category",
          data: this.xList,
          axisTick: {
            alignWithLabel: true
          },
          splitLine: {
            show: false   // 图标的背景网格
          },
          axisLabel: {
            textStyle: {
              color:'#FFF'  
            }
          },
          axisLine: {
            lineStyle: {
              color: '#FFF'
            }
          }
        },
        series: []
      };
    },
    pie1SetOptionFun(charts) {
      debugger
      var series = [];
      let yName = this.yText.map(function(item) {
        return item[0];
      });

      let innerRadius = this.yText.map(function(item) {
        return item[1];
      });

      let outSideRadius = this.yText.map(function(item) {
        return item[2];
      });
      
      for (var i=0;i<this.yList.length;i++){
        let pieData = [];

        let nameList = this.yList[i].map(function(item) {
          return item[0];
        });
        let valueList = this.yList[i].map(function(item) {
          return item[1];
        });

        for (let index in nameList) {
          pieData.push({
            value: valueList[index],
            name: nameList[index]
          });
        }
        let serie = {
            name: yName[i],
            type:'pie',
            center: ["50%", "60%"],
            radius : [innerRadius[i], outSideRadius[i]],
            data: pieData,
            itemStyle : {
                emphasis: {
                  shadowBlur: 10,
                  shadowOffsetX: 0,
                  shadowColor: "rgba(0, 0, 0, 0.5)"
                },
                normal : {
                    label : {
                        show : false
                    },
                    labelLine : {
                        show : false
                    }
                },
                emphasis : {
                    label : {
                        show : true,
                        position : 'center',
                        textStyle : {
                            fontSize : '12',
                            fontWeight : 'bold'
                        }
                    }
                }
            }
        }
        series.push(serie);
      }
      
      charts.setOption({
        series: series
      });
    },
    pieSetOptionFun(charts) {
      debugger
      var series = [];
      let yName = this.yText.map(function(item) {
        return item[0];
      });

      let innerRadius = this.yText.map(function(item) {
        return item[1];
      });
      let nameList = this.yList.map(function(item) {
        return item[0];
      });
      let valueList = this.yList.map(function(item) {
        return item[1];
      });

      let pieData = [];

      for (let index in nameList) {
        pieData.push({
          value: valueList[index],
          name: nameList[index]
        });
      }
      let serie = {
          name: yName[0],
          type:'pie',
          center: ["50%", "60%"],
          radius : innerRadius[0],
          data: pieData,
          itemStyle : {
              emphasis: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: "rgba(0, 0, 0, 0.5)"
              },
              normal : {
                  label : {
                      show : false
                  },
                  labelLine : {
                      show : false
                  }
              },
              emphasis : {
                  label : {
                      show : true,
                      position : 'center',
                      textStyle : {
                          fontSize : '12',
                          fontWeight : 'bold'
                      }
                  }
              }
          }
      }
      series.push(serie);

      
      charts.setOption({
        series: series
      });
    },
    generatorPieOption() {
      return {
        title: {
          text: this.titleText,
          subtext: this.subText,
          x: "center"
        },
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b} : {c} ({d}%)",
          position: function(point, params, dom, rect, size){ // point: 鼠标位置
            return this.getPositon(point, params, dom, rect, size);    
          }
        },
        legend: {
          orient: "horizontal",   // 布局方式，默认为水平布局，可选为：'horizontal' | 'vertical'
          x: 'center',
          data: this.legendData,
          itemWidth: 10,
          itemHeight: 8,
          textStyle: {
            color: '#FFF',
            fontSize: 10
          }
        },
        color:this.colorData,
        series: []
      };
    }
  },
  watch: {},
  mounted() {
    this.drawChart();
  },
  created() {
    //this.generatorWithAndHeight();
  }
};
</script>

<style scoped>
.chart {
  text-align: center;
  margin: 0 auto;
  position: relative;
  left: 10%;
  margin-left: -10%;
}
</style>