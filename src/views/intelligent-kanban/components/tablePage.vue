<template>
    <v-table
            is-horizontal-resize
            style="width:285px"
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
export default {
    
}
</script>

<script>
export default{
   props:{
       tableData:{
           type:Object,
           required: true
       },
       columns:{
           type:Object,
           required: true
       }
   },
   create(){
       
   },
    data() {
            return {
                   tableData:null,
                   columns:null

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