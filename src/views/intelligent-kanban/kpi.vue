<template>
  <!-- <div class="container">
    <el-card class="box-card">
      <div class="head">
        <span style="color:white">生产绩效</span>
      </div>
      <Shengchanjixiao />
    </el-card>
  </div> -->
  <el-row class="container">
    <el-col :span="12">
      <div class="grid-content bg-purple">
        <Product style="width:45%,height:50%" />
      </div>
    </el-col>
    <el-col :span="12">
      <div class="grid-content bg-purple">
        <Product style="width:45%,height:50%" />
      </div>
    </el-col>
  </el-row>
</template>

<script>
import Product from './pie/product-perform'

export default {
  name: 'LineChart',
  components: { Product }
}
</script>

<style scoped>
.container{
    background: #08263a;
    width: 100%;
    height: calc(100vh - 84px);
}
.card{
    width: 500px;
    height: 500px;
    border-color: rgb(23, 23, 119);
    border-width: 2;
    background: rgb(15, 65, 158);
}
.head{
   border-width: 2px;
   border-color: aliceblue;
   border-style: solid;
   width: 50%;
}
.box-card{
    background:none;
    width: 0.5*width;
}
</style>
