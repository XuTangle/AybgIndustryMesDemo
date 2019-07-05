<template>
  <div class="deviceStatistics-container">
      <div class="top"><span>XX分厂/XX车间/XX设备</span></div>
        <div class="main">
          <div class="left">
            <div class="main-left1 divBorder">
              <div class="title">设备腐蚀</div>
              <charts :chartData="chartData1" chartType="bar" ref="bar"></charts>
            </div>
            <div class="main-left2 divBorder">
              <div class="title">设备磨损</div>
              <charts :chartData="chartData2" chartType="pie" ref="pie"></charts>
            </div>
          </div>
          <div class="main-center">
          1234556
          </div>
          <div class="right">
            <div class="main-right1 divBorder">
            <div class="title">设备泄露</div>
            <charts :chartData="chartData" chartType="bar" ref="bar"></charts>
            </div>
            <div class="main-right2 divBorder">
              <div class="title">设备结垢</div>
              <charts :chartData="chartData" chartType="bar" ref="bar"></charts>
            </div>
          </div>
        </div>

        <div class="bottom">
          <div class="bottom-left">
            <div class="title">设备结垢</div>
            <charts :chartData="chartData" chartType="bar" ref="bar"></charts>
          </div>
          <div class="bottom-right">
            <div class="title">设备结垢</div>
            <charts :chartData="chartData" chartType="bar" ref="bar"></charts>
          </div>
        </div>
  </div>
</template>


<script>
import charts from "./components/charts";
export default {
  name: "chartsDemo",
  components: {
    charts
  },
  data() {
    return {
      tabPosition: "pie",
      chartData1: [["类别1", 100], ["类别2", 20], ["类别3", 30], ["类别3", 70]],
      chartData2: [["类别11", 100], ["类别22", 20], ["类别33", 30], ["类别33", 70]],
      chartRefs: ["pie"]
    };
  },
  props: {},
  computed: {},
  methods: {
    
  },
  watch: {

  },
  created() {
    console.log(1111111111);
  }
};
</script>

<style scoped>
.deviceStatistics-container {
    background: #ADD8E6;
    position: relative;
    width: 100%;
    height: calc(100vh - 84px);
 }

 .top span {
   height:7%;
   line-height: 35px;
   margin-left:5px;
 }
 .main {
   height:65%;
   display:flex;
   flex-warp:warp;
 }
 
 .main-center {
   width:40%;
   height:65%;
 }
 .left {
   width:30%;
   height:65%;
 }
  .right {
   width:30%;
   height:65%;
 }
.main-left1 {
   width:99%;
   height:75.5%;
   margin-bottom:3px;
 }
 .main-left2 {
   width:99%;
   height:75.5%;
 }
  .main-right1 {
   width:98%;
   height:75.5%;
   margin-bottom:3px;
 }
 .main-right2 {
   width:98%;
   height:75.5%;
 }
 .title {
   width:100%;
   padding:2px 1px 5px 5px;
   background:rgba(0,0,255,0.5);
   opacity: 0.85;
 }
 .divBorder {
   margin-left:5px;
	 border:0.9px solid #F00;
 }
 .bottom {
   width:100%;
   height:50%;
 }
 .bottom-left {
   width:49%;
   height:56%;
   float: left;
   margin-left:5px;
   border:0.9px solid #F00;
 }
 .bottom-right {
   width:50%;
   height:56%;
   float: right;
   margin-right:5px;
   border:0.9px solid #F00;
 }
</style>
