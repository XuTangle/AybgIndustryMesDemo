<template>
  <div class="window">
    <div class="aside">
      <div class="asidTop">
        <div class="clock"></div>
        <span>安全生产天数：1066天</span>
      </div>
      <div class="asideMain">
        <span>公司简介</span>
        <div class="introduction" id="scroll-message">
          <ul id="scroll1">
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
            <li>我们公司最棒！！！</li>
          </ul>
        </div>
      </div>
      <div class="asidefoot">
        <span>调度信息</span>
        
        <div class="information">
          <table>
          <th>
            <td>监控项目</td>
            <td>报警级别</td>
            <td>所属区域</td>
          </th>
        </table>
        <div id="scorllTale">
           <ul>
            <li class="liContent" v-for="item in contentList" :key="item">
              <div style="width:40vmin">
               {{item.project}}
              </div>
              <div>
                {{item.le}}
              </div>
              <div>
                {{item.region}}
              </div>
            </li>
          </ul>
        </div>
        </div>
        <div class="log">
          <span style="font-size:2vmin">调度日志</span>
          <div id="dispatch">
            <ul>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
              <li>我们公司最棒！！！</li>
          </ul>
          </div>
        </div>
      </div>
    </div>
    <div class="main">
      <div class="title">
        <span class="titleContent">XX钢厂全流程生产总览</span>
      </div>
      <div class="mainMain">
        <div id="lineChart" class="mainTop"></div>
        <div class="mainFoot">
          <companyItem
            v-for="key in dataList"
            :key="key"
            :title="key.title"
            :content="key.content"
            :admission="key.admission"
            :test="key.test"
            :state="key.state"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import echarts from "echarts";
import companyItem from "./companyItem";
// import { fetchData } from "@/api/Intelligence/overview";

export default {
  data() {
    return {
       dataList: [{
          title: '原料厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        },
        {
          title: '烧结厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        },
        {
          title: '炼铁厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        },
        {
          title: '炼铁厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        },
        {
          title: '炼铁厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        },
        {
          title: '炼铁厂',
          content: [{
            head: '巴西矿',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'FMG',
            dayValue: '3000',
            monthValue: '15000'
          },
          {
            head: 'PB',
            dayValue: '3000',
            monthValue: '15000'
          }
          ],
          admission: 0,
          test: 0,
          state: 0
        }
        ],
        contentList:[
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"},
          {project:"高炉1#水冷管温度",le:"高",region:"2#高炉"}
        ]
    };
  },
  created() {
    //   this.scollor();
    // fetchData().then(response => {
    //   this.dataList = response.data.dataList;
    // });
  },
  components: { companyItem },
  mounted() {
    this.initChart();
    this.scoller("scroll-message");
    this.scoller("scorllTale");
    this.scoller("dispatch")
  },
  methods: {
    scoller(byId){
      setTimeout(function(){
      var table = document.getElementById(byId);
       var timer = null;
       table.scrollTop = 0;
       table.innerHTML += table.innerHTML;
       function play() {
           clearInterval(timer);
           timer = setInterval(function() {
               table.scrollTop++;
               if (table.scrollTop >= table.scrollHeight / 2) {
                   table.scrollTop = 0;
               }
           }, 100);
       }
       setTimeout(play, 500);
       table.onmouseover = function() {
           clearInterval(timer)
       };

       table.onmouseout = play;
   },0)
    },
    initChart() {
      this.chart = echarts.init(document.getElementById("lineChart"));

      this.chart.setOption({
        tooltip: {
          trigger: "axis",
          axisPointer: {
            // 坐标轴指示器，坐标轴触发有效
            type: "shadow" // 默认为直线，可选为：'line' | 'shadow'
          }
        },
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          top: "10%",
          containLabel: true
        },
        xAxis: {
          type: "value",
          show: false
        },
        yAxis: {
          type: "category",
          data: ["冷轧钢", "管线钢", "SPHC"],
          splitLine: {
            show: false
          },
          axisTick: {
            show: false
          },
          axisLine: {
            show: false
          }
        },
        series: [
          {
            name: "已完成",
            type: "bar",
            stack: "总量",
            label: {
              normal: {
                show: true,
                position: "insideRight"
              }
            },
            data: [320, 302, 301]
          },
          {
            name: "未完成",
            type: "bar",
            stack: "总量",
            label: {
              normal: {
                show: true,
                position: "insideRight"
              }
            },
            data: [120, 132, 101],
            barGap: 20,
            barWidth: 25
          }
        ]
      });
    }
  }
};
</script>

<style scoped>
div {
  /* border: solid 1px black */
}
.window {
  display: flex;
  flex-direction: row;
}
.aside {
  width: 25.5%;
  /* border: solid 1px black; */
}
.asidTop,
.asideMain,.asidefoot {
  width: 96%;
  height: 33vmin;
  margin-top: 1vmin;
  margin-left: 1vmin;
  border: solid 0.5px black;
}
.asidefoot{
  height: 32vmin;
}
.asideMain {
  height: 30vmin;
}
.clock {
  height: 29vmin;
}
ul{
  padding:0;margin:0;
  padding-left: 1vmin
}
li{
  padding:0;
  margin:0;
  font-size: 1.7vmin;
   height: 3vmin;
}
.introduction {
  margin: 1vmin;
  height: 24vmin;
  border: solid 0.5px black;
  overflow:hidden;
    /* float:right; */
  /* padding-right:5%; */
}
.information{
  height: 15vmin;
  margin: 1vmin;
  border: solid 0.5px black;
}
.log{
  height: 11vmin;
  margin: 1vmin;
  border: solid 0.5px black;
}
.main {
  width: 74%;
  height: 99vmin;
  /* border: solid 1px black; */
}
.title {
  height: 13vmin;
  align-items: center;
  display: flex;
  justify-content: center;
}
.titleContent {
  font-size: 5vmin;
}
.mainMain {
  height: 85vmin;
  border: solid 0.5px black;
}
.mainTop {
  height: 30vmin;
}
.mainFoot {
  height: 56vmin;
  display: flex;
  flex-wrap: wrap;
}
#scorllTale{
  height: 11vmin;
  overflow:hidden;
  /* border: solid 0.5px black; */
}
#dispatch{
  height: 8vmin;
   overflow:hidden;
   /* border: solid 0.5px black; */
}
#scorllTale li{
  list-style: none;
}
table{
  width: 100%
}
td{
  width: 40%;
  text-align: left;
  font-size: 1.8vmin
}
.liContent{
  height: 3vmin;
  display: flex;
  flex-direction: row;
}
.liContent div{
  width: 50%
}
</style>
