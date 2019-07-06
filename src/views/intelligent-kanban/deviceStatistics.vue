<template>
  <div class="deviceStatistics-container">
      <div class="top"><span>XX分厂/XX车间/XX设备</span></div>
        <div class="main">
          <div class="left">
            <div class="main-left1 divBorder">
              <div class="title">设备腐蚀</div>
              <!-- <charts chartType="bar1"  :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" :stackFlag="stackFlag"></charts> -->
              <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" ></charts>
            </div>
            <div class="main-left2 divBorder">
              <div class="title">设备磨损</div>
              <!-- <charts chartType="line" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2"></charts> -->
              <charts chartType="pie1" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2"></charts>
              <!-- <charts chartType="pie" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2"></charts> -->
              <!-- <charts chartType="bar" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2"></charts> -->
            </div>
          </div>
          <div class="main-center">
            <div class="main-center-top deviceInfo">
              <div style="padding:20px 10px;width:33%;float:left">
                A1</br>
                测点列表</br>
                速度：3.1mm/s(2019-6-6 15:30:18)</br>
                温度：108°(2019-6-6 15:30:18</br>
              </div>
              <div style="padding:20px 10px;width:33%;float:right">
                A2</br>
                测点列表</br>
                速度：3.2mm/s(2019-6-6 15:30:18)</br>
                温度：105°(2019-6-6 15:30:18)</br>
              </div>
              
            </div>
            <div class="main-center-bottom deviceInfo">
              <div style="padding:0px 10px;width:33%;float:left">
                B1</br>
                测点列表</br>
                速度：3.1mm/s(2019-6-6 15:30:18)</br>
                温度：106°(2019-6-6 15:30:18)</br>
              </div>
              <div style="padding:0px 10px;width:33%;float:right">
                B2</br>
                测点列表</br>
                速度：3.3mm/s(2019-6-6 15:30:18)</br>
                温度：103°(2019-6-6 15:30:18)</br>
              </div>
              
              <div style="width:100%;position:absolute;left:170px;bottom:-90px">
                B3</br>
                测点列表</br>
                速度：3.3mm/s(2019-6-6 15:30:18)</br>
                温度：103°(2019-6-6 15:30:18)</br>
              </div>
              <img src="../../../public/static/device.png" width="30%" height="70%" style="position:absolute;top:80px" />
            </div>
          </div>
          <div class="right">
            <div class="main-right1 divBorder">
            <div class="title">设备泄露</div>
            <charts chartType="bar" :xList="xList_right1" :yList="yList_right1" :xText="xText_right1" :yText="yText_right1"></charts>
            </div>
            <div class="main-right2 divBorder">
              <div class="title">设备结垢</div>
              <charts chartType="bar" :xList="xList_right2" :yList="yList_right2" :xText="xText_right2" :yText="yText_right2"></charts>
            </div>
          </div>
        </div>

        <div class="bottom">
          <div class="bottom-left">
            <div class="title">设备运行时效分析</div>
            <charts chartType="bar"  :xList="xList_bottom1" :yList="yList_bottom1" :xText="xText_bottom1" :yText="yText_bottom1" :stackFlag="stackFlag"></charts>
          </div>
          <div class="bottom-right">
            <div class="title">设备停运时间统计分析</div>
            <charts chartType="bar" :xList="xList_bottom2" :yList="yList_bottom2" :xText="xText_bottom2" :yText="yText_bottom2"></charts>
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
      // tabPosition: "bar",
      // chartRefs: ["line", "bar", "pie"],
       chartData: [["类别1", 100], ["类别2", 20], ["类别3", 30], ["类别3", 70]],
      // chartData2: [["类别11", 100], ["类别22", 20], ["类别33", 30], ["类别33", 70]],
      
     
      // X  Y轴交换位置Demo  响应的html代码也有修改 chartType=bar
      // xList_left1:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      // yList_left1:[[100,20,50,70],[30,60,70,28],[70,80,20,98],[10,80,50,38]],
      // xText_left1:'设备腐蚀',  // x坐标的提示信息
      // yText_left1:[['点蚀','bar','#a6d192'],['缝隙腐蚀','bar','#99bce0'],['磨损腐蚀','bar','#767db9'],['应力腐蚀','bar','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据
      
      stackFlag : true,   // 状态图是否要堆积数据 默认false

      xList_left1:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      yList_left1:[[100,20,50,70],[30,60,70,28],[70,80,20,98],[10,80,50,38]],
      xText_left1:'设备腐蚀',  // x坐标的提示信息
      yText_left1:[['点蚀','bar','#a6d192'],['缝隙腐蚀','bar','#99bce0'],['磨损腐蚀','bar','#767db9'],['应力腐蚀','bar','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据
      

      // xList_left2:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      // yList_left2:[[50],[20],[30],[90]],
      // xText_left2:'设备磨损',  // x坐标的提示信息
      // yText_left2:[['设备磨损率','bar','#a9d289']],   // y坐标的提示信息，chart类型，以及颜色数据

      // 环形图demo 
      xList_left2:[['制造成本','#a6d192'],['产量','#99bce0'],['质量','#767db9'],['安全环保','#0ca2a3']],
      yList_left2:[[['制造成本',25],['产量',12],['质量',34],['安全环保',29]],[['制造成本',45],['产量',9],['质量',27],['安全环保',19]]],
      xText_left2:'生产绩效',  // x坐标的提示信息
      yText_left2:[['分厂1','50%','70%'],['分厂2','30%','45%']],   // y坐标的提示信息，chart类型，以及颜色数据

      // 折现demo
      // xList_left2:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      // yList_left2:[[100,20,50,70],[30,60,70,28],[70,80,20,98],[10,80,50,38]],
      // xText_left2:'设备腐蚀',  // x坐标的提示信息
      // yText_left2:[['点蚀','#a6d192'],['缝隙腐蚀','#99bce0'],['磨损腐蚀','#767db9'],['应力腐蚀','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据
      
      // 饼图demo 
      // xList_left2:[['制造成本','#a6d192'],['产量','#99bce0'],['质量','#767db9'],['安全环保','#0ca2a3']],
      // yList_left2:[['制造成本',25.28],['产量',77.56],['质量',34.49],['安全环保',46.22]],
      // xText_left2:'生产绩效',  // x坐标的提示信息
      // yText_left2:[['生产绩效','50%']],   // y坐标的提示信息，chart类型，以及颜色数据

      xList_right1:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      yList_right1:[[70],[60],[20],[50]],
      xText_right1:'设备泄露',  // x坐标的提示信息
      yText_right1:[['泄漏率','bar','#9abcdf']],  // y坐标的提示信息，chart类型，以及颜色数据

      xList_right2:['锅炉1','锅炉2','管道1','管道2'],
      yList_right2:[[10],[30],[60],[70]],
      xText_right2:'设备结垢',  // x坐标的提示信息
      yText_right2:[['结垢率','bar','#7b7cbb']],   // y坐标的提示信息，chart类型，以及颜色数据

      xList_bottom1:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      yList_bottom1:[[100,20,50,70],[30,60,70,28],[70,80,20,98]],
      xText_bottom1:'设备运行时效分析',  // x坐标的提示信息
      yText_bottom1:[['运行小时','bar','#a2cd8a'],['备用小时','bar','#97bddf'],['可用小时','bar','#97bddf']], // y坐标的提示信息，chart类型，以及颜色数据

      xList_bottom2:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      yList_bottom2:[[20,20,50,70],[30,60,70,28],[70,80,20,98],[70,80,20,98]],
      xText_bottom2:'设备停运时间统计分析',  // x坐标的提示信息
      yText_bottom2:[['计划停运小时','bar','#a6d28e'],['非计划停运小时','bar','#99bce2'],['平均计划停运小时','line','#4006ef'],['平均非计划停运小时','line','#a559d5']]  // y坐标的提示信息，chart类型，以及颜色数据
      
    };
  },
  props: {},
  computed: {},
  methods: {
    
  },
  watch: {

  },
  created() {
  }
};
</script>

<style scoped>
.deviceStatistics-container {
    background:url('../../../public/static/bg.jpg');
    position: relative;
    width: 100%;
    height: calc(100vh - 84px);
    color:#FFF;
 }

 .top span {
   height:7%;
   line-height: 35px;
   margin-left:5px;
 }
 .main {
   height:65%;
   display:flex;
 }
 
 .main-center {
   position: relative;
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
   background:#124d72;
   opacity: 0.8;
 }
 .divBorder {
   margin-left:5px;
	 border:1.5px solid #124d72;
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
   border:1.5px solid#124d72;
 }
 .bottom-right {
   width:50%;
   height:56%;
   float: right;
   margin-right:2px;
   border:1.5px solid #124d72;
 }
 .main-center-top {
   width:100%;
   height:75.5%;
 }
 .main-center-bottom {
   width:100%;
   height:75.5%;
   margin-top:3px;
 }
 .deviceInfo {
   font-size: 10px
 }
</style>
