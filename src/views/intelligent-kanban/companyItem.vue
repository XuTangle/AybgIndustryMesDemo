<template>
  <div class="item">
    <div class="title">
      <span>{{title}}</span>
    </div>
    <div class="mainTable">
      <table>
        <tr>
          <td></td>
          <td>日累计</td>
          <td>月累计</td>
        </tr>
        <tr v-for="item in content" :key="item">
          <td>{{item.head}}</td>
          <td>{{item.dayValue}}吨</td>
          <td>{{item.monthValue}}吨</td>
        </tr>
      </table>
    </div>
    <div class="mainFoot">
      <div class="one">
        <p class="number" id="adm" :style="typeColor">{{admission}}</p>
        <p>入场</p>
      </div>
      <div class="one">
        <p class="number test" :style="testColor">{{test}}</p>
        <p>检验</p>
      </div>
      <div class="one">
        <p class="number state" :style="stateColor">{{state}}</p>
        <p>运行状态</p>
      </div>
    </div>
  </div>
</template>
<script>
import { truncate } from "fs";
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    content: {
      type: Array,
      required: true
    },
    admission: {
      type: Number,
      required: true
    },
    test: {
      type: Number,
      required: true
    },
    state: {
      type: Number,
      required: true
    },
  },
  created() {
    // debugger;
    if (this.admission == 0) {
      this.typeColor="background-color:yellow"
    }
  },
  data() {
    return {
        typeColor:"background-color:aqua",
        stateColor:"background-color:aqua",
        testColor:"background-color:aqua",
        content:null
    };
  }
};
</script>
<style scoped>
.item {
  width: 30%;
  height: 23vmin;
  margin-left:2%;
  margin-top: 2vmin;
  margin-right: 1%;
  border: solid 0.5px black;
}
.title {
  align-items: center;
  display: flex;
  justify-content: center;
}
table td {
  width: 13vmin;
  font-size: 2vmin;
}
table {
  margin: 1vmin 3vmin;
}
.one {
  width: 9vmin;
  font-size: 2vmin;
  margin-left: 3vmin;
}
p {
  padding: 0;
  margin: 0;
}
.number {
  width: 4vmin;
  /* background-color: aqua; */
  align-items: center;
  display: flex;
  justify-content: center;
}
.mainFoot {
  display: flex;
  flex-direction: row;
}
</style>
