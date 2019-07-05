<template>
  <div class="container">
    <div class="card">
      <div class="card-head">
        <span>生产绩效</span>
      </div>
      
         <ProductPerform />
         <TablePerform  />
    
    </div>
    <div class="card">
      <div class="card-head">
        <span>生产消耗</span>
      </div>
      <ProductConsumption />
    </div>
    <div class="card">
      <div class="card-head">
        <span>生产产量</span>
      </div>
      <ProductPerform />
    </div>
    <div class="card">
      <div class="card-head">
        <span>原料库存</span>
      </div>
      <ProductPerform />
    </div>
  </div>
</template>

<script>
import ProductPerform from './kpi/components/product-perform'
import ProductConsumption from './kpi/components/product-consumption'
import TablePerform from './kpi/table/perform'
export default {
  name: 'LineChart',
  components: { ProductPerform, ProductConsumption, TablePerform }
}
</script>

<style scoped>
.container{
    background: #08263a;
    width: 100%;
    height: calc(100vh - 84px);
    display: flex;
    flex-wrap: wrap;
}
.card{
    width: 50%;
    height:50%;
    border-color: rgb(23, 23, 119);
    border-width: 2;
    border-style: solid;
    background: #08263a;
    display: flex;
    flex-wrap: wrap;
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
  background: rgb(4, 52, 124);
  color: aliceblue;
  height: 10%;
  display: flex;
  align-items: center;
  padding-left: 20px;
  font-weight: 600;
  letter-spacing: 3px;
  width: 100%;
}

</style>
