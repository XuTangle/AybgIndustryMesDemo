<template>
  <div class="container">
   
    <div class="card">
      <div class="card-head">
        <span>生产产量</span>
      </div>
      <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" style="width: 55%" ></charts>
      <TablePage class="tables"  />
    </div>
    <div class="card">
      <div class="card-head">
        <span>原料库存</span>
      </div>
      <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" style="width: 55%" ></charts>
      <TablePage class="tables"  />
    </div>
     <div class="card">
      <div class="card-head">
        <span>生产绩效</span>
      </div>
      
        <charts chartType="pie1" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2" style="width: 55%"></charts>
         <TablePage class="tables"  />
    
    </div>
    <div class="card">
      <div class="card-head">
        <span>生产消耗</span>
      </div>
      <charts chartType="pie1" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2" style="width: 50%"></charts>
      <TablePage class="tables"  />
    </div>
     <div class="card">
      <div class="card-head">
        <span>生产绩效</span>
      </div>
      
         <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" style="width:55%" ></charts>
         <TablePage class="tables"  />
    
    </div>
    <div class="card">
      <div class="card-head">
        <span>生产消耗</span>
      </div>
      <charts chartType="bar" :xList="xList_bottom2" :yList="yList_bottom2" :xText="xText_bottom2" :yText="yText_bottom2" style="width: 55%"></charts>
      <TablePage class="tables"  />
    </div>
        <div class="card">
      <div class="card-head">
        <span>生产产量</span>
      </div>
      <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" style="width: 55%"></charts>
    </div>
    <div class="card">
      <div class="card-head">
        <span>原料库存</span>
      </div>
      <charts chartType="bar1" :xList="xList_left3" :yList="yList_left3" :xText="xText_left3" :yText="yText_left3" style="width: 55%" ></charts>
      <TablePage :datasource="datasource"></TablePage>
    </div>
  </div>
</template>

<script>
import charts from "./components/charts";
import TablePage from './components/tablePage'
export default {
  name: 'LineChart',
  components: {  charts,TablePage },
   data() {
    return {
      datasource:[{'id': '1', 'name': '小红', 'age': '12'},
                  {'id': '2', 'name': '小丽', 'age': '12'},
                  {'id': '2', 'name': '小丽', 'age': '12'}],
      // tabPosition: "bar",
      // chartRefs: ["line", "bar", "pie"],
       chartData: [["类别1", 100], ["类别2", 20], ["类别3", 30], ["类别3", 70]],
      // chartData2: [["类别11", 100], ["类别22", 20], ["类别33", 30], ["类别33", 70]],
      
     
      // X  Y轴交换位置Demo  响应的html代码也有修改 chartType=bar
      xList_left3:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      yList_left3:[[100,20,50,70],[30,60,70,28],[70,80,20,98],[10,80,50,38]],
      xText_left3:'设备腐蚀',  // x坐标的提示信息
      yText_left3:[['点蚀','bar','#a6d192'],['缝隙腐蚀','bar','#99bce0'],['磨损腐蚀','bar','#767db9']], // y坐标的提示信息，chart类型，以及颜色数据
      
      stackFlag : true,   // 状态图是否要堆积数据 默认false

      xList_left1:['SPHC','冷轧料','管线钢','低合金钢'],
      yList_left1:[[100,20,50,70],[30,60,70,28],[70,80,20,98],[10,80,50,38]],
      xText_left1:'设备腐蚀',  // x坐标的提示信息
      yText_left1:[['当前产量','bar','#a6d192'],['月计划','bar','#99bce0'],['上月实绩','bar','#767db9'],['应力腐蚀','bar','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据
      

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
}
</script>

<style scoped>
.container{
    background:url('../../../public/static/bg.jpg');
    position: relative;
    width: 100%;
    height: calc(100vh - 84px);
    color:#FFF;
    display: flex;
    flex-wrap: wrap;
    overflow:auto;
}
.card{
    width: 50%;
    height:50%;
    border-color: rgb(23, 23, 119);
    border-width: 2;
    border-style: solid;
    /* background: #08263a; */
    display: flex;
    flex-wrap: wrap;
    overflow: hidden;
}

.box-card{
    background:none;
    width: 0.5*width;
}
.pie{
    width: 100%;
    height: 100%;
    border-width: 2px;
    border-color: aliceblue;
    border-style: solid;
    }
.grid-content{
    border-width: 2px;
    border-color: aliceblue;
    border-style: solid;
}
.card-head{
    background:#124d72;
   opacity: 0.8;
  color: aliceblue;
  height: 10%;
  display: flex;
  align-items: center;
  padding-left: 20px;
  font-weight: 600;
  letter-spacing: 3px;
  width: 100%;
}
.tables{
margin-left:0px;
margin-top: 20px;
}

</style>
