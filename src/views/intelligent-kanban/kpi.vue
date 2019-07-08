<template>
  <div class="container">
   
    <div class="card">
      <div class="card-head">
        <span>生产产量</span>
      </div>
      <charts chartType="bar" :xList="xList_left1" :yList="yList_left1" :xText="xText_left1" :yText="yText_left1" style="width: 53%" ></charts>
      <TablePage class="tables" :tableData="tableData1" :columns="columns1" />
    </div>
    <div class="card">
      <div class="card-head">
        <span>原料库存</span>
      </div>
      <charts chartType="bar" :xList="xList_right1" :yList="yList_right1" :xText="xText_right1" :yText="yText_right1" style="width: 53%" ></charts>
      <TablePage class="tables" :tableData="tableData2" :columns="columns2" />
    </div>
     <div class="card">
      <div class="card-head">
        <span>生产绩效</span>
      </div>
      
        <charts chartType="pie1" :xList="xList_left2" :yList="yList_left2" :xText="xText_left2" :yText="yText_left2" style="width: 53%"></charts>
         <TablePage class="tables" :tableData="tableData3" :columns="columns3"  />
    
    </div>
    <div class="card">
      <div class="card-head">
        <span>生产消耗</span>
      </div>
     <charts chartType="pie1" :xList="xList_left4" :yList="yList_left4" :xText="xText_left4" :yText="yText_left4" style="width: 53%"></charts>
      <TablePage class="tables"  :tableData="tableData4" :columns="columns4" />
    </div>
     <div class="card">
      <div class="card-head">
        <span>设备运行指标</span>
      </div>
      
         <charts chartType="bar" :xList="xList_left5" :yList="yList_left5" :xText="xText_left5" :yText="yText_left5" style="width:53%" ></charts>
         <TablePage class="tables" :tableData="tableData5" :columns="columns5" />
    
    </div>
    <div class="card">
      <div class="card-head">
        <span>能耗指标</span>
      </div>
       <charts chartType="bar" :xList="xList_left6" :yList="yList_left6" :xText="xText_left6" :yText="yText_left6" style="width:53%" ></charts>
      <TablePage class="tables" :tableData="tableData6" :columns="columns6"  />
    </div>
        <div class="card">
      <div class="card-head">
        <span>生产质量</span>
      </div>
      <charts chartType="bar" :xList="xList_left7" :yList="yList_left7" :xText="xText_left7" :yText="yText_left7" style="width: 53%"></charts>
      <TablePage class="tables" :tableData="tableData7" :columns="columns7"  />
    </div>
    <div class="card">
      <div class="card-head">
        <span>安环指标</span>
      </div>
      <charts chartType="bar1" :xList="xList_left3" :yList="yList_left3" :xText="xText_left3" :yText="yText_left3" style="width: 53%" ></charts>
      <TablePage class="tables" :datasource="datasource" :tableData="tableData8" :columns="columns8"></TablePage>
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
      xList_left3:['一月','二月','三月','四月','五月'],
      yList_left3:[[220,232,158,232,131],[231,132,110,223,258],[157,168,260,228,199]],
      xText_left3:'设备腐蚀',  // x坐标的提示信息
      yText_left3:[['安全','bar','#a6d192'],['环保','bar','#99bce0'],['健康','bar','#767db9']], // y坐标的提示信息，chart类型，以及颜色数据
      
      stackFlag : true,   // 状态图是否要堆积数据 默认false

      xList_left1:['SPHC','冷轧料','管线钢','低合金钢'],
      yList_left1:[[100,20,50,70],[30,60,70,28],[70,80,20,98]],
      xText_left1:'设备腐蚀',  // x坐标的提示信息
      yText_left1:[['当前产量','bar','#a6d192'],['月计划','bar','#99bce0'],['上月实绩','bar','#767db9']], // y坐标的提示信息，chart类型，以及颜色数据
      
      xList_left5:['一月','二月','三月','四月','五月'],
      yList_left5:[[54.90,36.62,57.46,55.89,46.99],[79.83,24.03,56.76,45.67,43.88]],
      xText_left5:'设备腐蚀',  // x坐标的提示信息
      yText_left5:[['完好率','bar','#a6d192'],['消缺率','bar','#99bce0']], // y坐标的提示信息，chart类型，以及颜色数据

      xList_left6:['一月','二月','三月','四月','五月'],
      yList_left6:[[36.55,84.67,17.71,84.03,48.16],[13.50,60.78,72.88,69.64,78.77],[27.08,75.73,46.05,47.66,37.63],[82.49,46.51,48.77,36.83,16.77]],
      xText_left6:'设备腐蚀',  // x坐标的提示信息
      yText_left6:[['水耗计划','bar','#a6d192'],['水耗实际','bar','#99bce0'],['电耗计划','bar','#767db9'],['电耗实际','bar','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据
      
      xList_left7:['SPHC','冷轧料','管线钢','低合金','优碳'],
      yList_left7:[[36.55,84.67,17.71,84.03,48.16],[13.50,60.78,72.88,69.64,78.77],[27.08,75.73,46.05,47.66,37.63],[82.49,46.51,48.77,36.83,16.77]],
      xText_left7:'设备腐蚀',  // x坐标的提示信息
      yText_left7:[['优等品','bar','#a6d192'],['合格','bar','#99bce0'],['不合格','bar','#767db9'],['一等品','bar','#0ca2a3']], // y坐标的提示信息，chart类型，以及颜色数据

      // xList_left2:['称重给煤机','斗式提升机','二次风机','高压流化风机'],
      // yList_left2:[[50],[20],[30],[90]],
      // xText_left2:'设备磨损',  // x坐标的提示信息
      // yText_left2:[['设备磨损率','bar','#a9d289']],   // y坐标的提示信息，chart类型，以及颜色数据

      // 环形图demo 
      xList_left2:[['制造成本','#a6d192'],['产量','#99bce0'],['质量','#767db9'],['安全环保','#0ca2a3']],
      yList_left2:[[['制造成本',25],['产量',12],['质量',34],['安全环保',29]],[['制造成本',45],['产量',9],['质量',27],['安全环保',19]]],
      xText_left2:'生产绩效',  // x坐标的提示信息
      yText_left2:[['分厂1','50%','70%'],['分厂2','30%','45%']],   // y坐标的提示信息，chart类型，以及颜色数据
      
      xList_left4:[['原料','#a6d192'],['辅料','#99bce0'],['设备','#767db9'],['能源','#0ca2a3']],
      yList_left4:[[['原料',362.72],['辅料',254.14],['设备',190.39],['能源',154.90]],[['原料',209.72],['辅料',196.43],['设备',398.10],['能源',203.62]]],
      xText_left4:'生产绩效',  // x坐标的提示信息
      yText_left4:[['分厂1','50%','70%'],['分厂2','30%','45%']],   // y坐标的提示信息，chart类型，以及颜色数据

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

      xList_right1:['铁矿石','煤炭','合金矿石','白灰'],
      yList_right1:[[100,20,50,70],[30,60,70,28],[70,80,20,98]],
      xText_right1:'设备腐蚀',  // x坐标的提示信息
      yText_right1:[['当前库存','bar','#a6d192'],['消耗量','bar','#99bce0'],['入库量','bar','#767db9']],

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
      yText_bottom2:[['计划停运小时','bar','#a6d28e'],['非计划停运小时','bar','#99bce2'],['平均计划停运小时','line','#4006ef'],['平均非计划停运小时','line','#a559d5']] , // y坐标的提示信息，chart类型，以及颜色数据
      

       tableData1: [
                       {"type":"SPHC","now":"47.69","plan":"55.18","lastmonth":"59.25"},
                       {"type":"冷轧料","now":"58.05","plan":"94.44","lastmonth":"26.82"},
                       {"type":"管线钢","now":"52.21","plan":"22.61","lastmonth":"52.42"},
                       {"type":"低合金","now":"52.85","plan":"40.71","lastmonth":"64.89"},
                       {"type":"优碳","now":"10.1","plan":"94.57","lastmonth":"83.96"}
                    ],
      columns1: [     {field: 'type', title:'（万吨）', width: 70,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'now', title:'当前产量', width: 70,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'plan', title: '月计划', width: 70, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'lastmonth', title: '上月实际', width: 70, titleAlign: 'center',columnAlign:'center',titleCellClassName:'title-cell-class-name-test',isResize:true},
                   
                   ],

       tableData2: [
                       {"type":"铁矿石","now":"81.78","plan":"12.99","lastmonth":"48.98"},
                       {"type":"煤炭","now":"26.51","plan":"29.65","lastmonth":"49.75"},
                       {"type":"合金矿石","now":"60.66","plan":"92.20","lastmonth":"14.01"},
                       {"type":"白灰","now":"30.49","plan":"28.07","lastmonth":"20.65"},
                        {"type":"  ","now":"","plan":"","lastmonth":""},
                      
                    ],
      columns2: [     {field: 'type', title:'（万吨）', width: 70,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'now', title:'当前产量', width: 70,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'plan', title: '月计划', width: 70, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'lastmonth', title: '上月实际', width: 70, titleAlign: 'center',columnAlign:'center',titleCellClassName:'title-cell-class-name-test',isResize:true},
                   
                   ],

       tableData3: [
                       {"type":"制造成本","one":"81.78","two":"12.99",},
                       {"type":"产量","one":"26.51","two":"29.65",},
                       {"type":"质量","one":"60.66","two":"92.20",},
                       {"type":"安全环保","one":"60.66","two":"92.20",},
                       {"type":"  ","now":"","plan":"","lastmonth":""},                      
                    ],
       columns3: [     {field: 'type', title:'种类', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'分厂1', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '分厂2', width: 93.33, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},              
                   ],

       tableData4: [
                       {"type":"原料","one":"81.78","two":"12.99",},
                       {"type":"辅料","one":"26.51","two":"29.65",},
                       {"type":"设备","one":"60.66","two":"92.20",},
                       {"type":"能源","one":"60.66","two":"92.20",},
                       {"type":"  ","now":"","plan":"","lastmonth":""},                      
                    ],
       columns4: [     {field: 'type', title:'种类', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'分厂1', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '分厂2', width: 93.33, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},              
                   ],

       tableData5: [
                       {"type":"一月","one":"54.90","two":"79.83",},
                       {"type":"二月","one":"36.62","two":"24.03",},
                       {"type":"三月","one":"57.46","two":"56.76",},
                       {"type":"四月","one":"55.89","two":"45.67",},
                       {"type":"五月 ", "one":"46.99","two":"43.88"},                      
                    ],


       columns5: [     {field: 'type', title:'%', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'完好率', width: 93.33,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '消缺率', width: 93.33, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},              
                   ],
       tableData6: [
                       {"type":"一月","one":"36.55","two":"79.83","three":"27.08","four":"82.49"},
                       {"type":"二月","one":"36.62","two":"24.03","three":"75.73","four":"46.51"},
                       {"type":"三月","one":"57.46","two":"56.76","three":"46.05","four":"48.77"},
                       {"type":"四月","one":"55.89","two":"45.67","three":"47.66","four":"36.83"},
                       {"type":"五月 ", "one":"46.99","two":"43.88","three":"37.63","four":"16.77"},                      
                    ],
       columns6: [    {field: 'type', title:'(万吨)', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'水耗计划', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '水耗实际', width: 56, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'three', title:'电耗计划', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'four', title: '电耗实际', width: 56, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},               
                   ],

        tableData7: [
                       {"type":"SPHC","one":"36.55","two":"79.83","three":"27.08","four":"82.49"},
                       {"type":"冷轧料","one":"36.62","two":"24.03","three":"75.73","four":"46.51"},
                       {"type":"管线钢","one":"57.46","two":"56.76","three":"46.05","four":"48.77"},
                       {"type":"低合金","one":"55.89","two":"45.67","three":"47.66","four":"36.83"},
                       {"type":"优碳", "one":"46.99","two":"43.88","three":"37.63","four":"16.77"},                      
                    ],
       columns7: [    {field: 'type', title:'%', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'优等品', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '合格', width: 56, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'three', title:'不合格', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'four', title: '一等品', width: 56, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},               
                   ],

        tableData8: [
                       {"type":"一月","one":"36.55","two":"79.83","three":"27.08","four":"82.49"},
                       {"type":"二月","one":"36.62","two":"24.03","three":"75.73","four":"46.51"},
                       {"type":"三月","one":"57.46","two":"56.76","three":"46.05","four":"48.77"},
                       {"type":"四月","one":"55.89","two":"45.67","three":"47.66","four":"36.83"},
                       {"type":"五月", "one":"46.99","two":"43.88","three":"37.63","four":"16.77"},                      
                    ],
       columns8: [    {field: 'type', title:'月份', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'one', title:'安全', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'two', title: '环保', width: 56, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'three', title:'健康', width: 56,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                     
                   ]            
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
margin-right: 10px;
margin-top: 20px;
}

</style>
