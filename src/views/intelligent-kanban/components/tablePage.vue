<template>
    <v-table
            is-horizontal-resize
            style="width:45%"
            :columns="columns"
            :table-data="tableData"
            :row-click="rowClick"
            :column-cell-class-name="columnCellClass"
            row-hover-color="#eee"
            row-click-color="#edf7ff"
    ></v-table>
</template>

<style>
.v-table-class{
    font-size: 14px;
    font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    color: rgb(255, 255, 255);
    background: #000;
}
    .title-cell-class-name-test{
        background-color: #0e3d5a;
        color:#fff;
    }
    .column-cell-class-name-test{
        background-color: #124d72
       
    }
    .column-cell-class-name-test .v-table-body-cell{
        border-color: #187;
    }
    .column-cell-class-name-test2 .v-table-body-cell{
        border-color: #2db7f5;
    }
</style>

<script>

export default{
   
        data() {
            return {
                   tableData: [
                       {"name":"赵伟","tel":"156*****1987","hobby":"钢琴、书法、唱歌","address":"上海市黄浦区金陵东路569号17楼"},
                       {"name":"李伟","tel":"182*****1538","hobby":"钢琴、书法、唱歌","address":"上海市奉贤区南桥镇立新路12号2楼"},
                       {"name":"孙伟","tel":"161*****0097","hobby":"钢琴、书法、唱歌","address":"上海市崇明县城桥镇八一路739号"},
                       {"name":"周伟","tel":"197*****1123","hobby":"钢琴、书法、唱歌","address":"上海市青浦区青浦镇章浜路24号"},
                       {"name":"吴伟","tel":"183*****6678","hobby":"钢琴、书法、唱歌","address":"上海市松江区乐都西路867-871号"}
                    ],
                   columns: [
                      {field: 'name', title:'姓名', width: 80,titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'tel', title: '手机号码', width: 100, titleAlign: 'center',columnAlign:'center',isResize:true,titleCellClassName:'title-cell-class-name-test'},
                      {field: 'hobby', title: '爱好', width: 100, titleAlign: 'center',columnAlign:'center',titleCellClassName:'title-cell-class-name-test',isResize:true},
                   
                   ]

            }
        },
        methods:{

            columnCellClass(rowIndex,columnName,rowData){

                // 给三行column为‘hobby’的列设置className
             if (rowIndex ===0||rowIndex===1||rowIndex===2||rowIndex===3||rowIndex===4||rowIndex===5){

                    return 'column-cell-class-name-test';
                }
            
            },

            rowClick(rowIndex,rowData){
               console.log(rowIndex);
               console.log(rowData);
            }
        }
    }
</script>