<template>
  <el-table
    :data="tableData"
    height="250"
    
    :header-cell-style="{background:'#08263a',color:'#606266'}">
    <el-table-column
    row-style="{background:'#08263a',color:'#606266'}"
      prop="date"
      label="种类"
      width="110%">
    </el-table-column>
    <el-table-column
      prop="name"
      label="分厂1"
      width="110%">
    </el-table-column>
    <el-table-column
      prop="address"
      label="分厂2"
      width="110%">
    </el-table-column>
  </el-table>
</template>
<style scoped>
.el-table-column{
   background: #f00;
  }
  .el-table td,.building-top .el-table th.is-leaf {
    border-bottom:  1px solid #ccc;
}
</style>

<script>
  export default {
    data() {
      return {
        tableData: [{
          date: '制造成本',
          name: '25.28',
          address: '65.41'
        }, {
          date: '产量',
          name: '77.56',
          address: '25.13'
        }, {
          date: '质量',
          name: '34.49',
          address: '27.47'
        }, {
          date: '安全环保',
          name: '46.22',
          address: '50.85'
        }],
      }
    }
  }
</script>