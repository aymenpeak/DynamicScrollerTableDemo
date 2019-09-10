<template>
  <div class="home">
    <div class="btn-container">
      <button @click="prevPage()" style="margin-right:5px;">Prev page</button>
      <button @click="nextPage()">Next page</button>
    </div>
    
    <DynamicScroller
      :items="tableData"
      :min-item-size="30"
      class="scroller Rtable Rtable--3cols "
      key-field="guid"
      page-mode
    >
      <div
        slot="before"
        class="Rheader"
      >
       <div class="Rtable-cell thead" v-for="head in headers" :key="head">
         {{head}}
         </div>
      </div>

      <template slot-scope="{ item, index, active }">
        <DynamicScrollerItem
          :item="item"
          :index="index"
          :active="active"
          :data-index="index"
          :data-active="active"
          class="message"
        >
          <div class="Rtable-cell">
            {{ item.name }}
          </div>
          <div class="Rtable-cell">
            {{ item.isActive }}
          </div>
          <div class="Rtable-cell">
            {{ item.balance }}
          </div>
          <div class="Rtable-cell">
            {{ item.age }}
          </div>
          <div class="Rtable-cell">
            {{ item.eyeColor }}
          </div>
          <div class="Rtable-cell">
            {{ item.name }}
          </div>
          <div class="Rtable-cell">
            {{ item.gender }}
          </div>
          <div class="Rtable-cell">
            {{ item.company }}
          </div>
          <div class="Rtable-cell">
            {{ item.phone }}
          </div>
          
         
        </DynamicScrollerItem>
      </template>
    </DynamicScroller>
  </div>
</template>

<script>
import rows from "../utils/data";
import rowsForNextPage from "../utils/nextPage";
import { DynamicScroller } from "vue-virtual-scroller";
import "vue-virtual-scroller/dist/vue-virtual-scroller.css";

export default {
  name: 'home',
  components: {
    DynamicScroller
  },
  data() {
    return {
      tableData: rows,
      headers: ["index", "isActive", "balance",
      "age","eyeColor","name","gender","company","phone"]
      }
  },
  methods: {
    nextPage(){
      this.tableData = rowsForNextPage;
    },
    prevPage(){
      this.tableData = rows ;
    }
  }

}
</script>
<style >

.dynamic-scroller-demo,
.scroller {
    width: 100%;
  height: 100%;
  overflow-y: auto;
}
.dynamic-scroller-demo {
  overflow: hidden;
}
.notice {
  padding: 24px;
  font-size: 20px;
  color: #999;
}
.message {
  display: flex;
  min-height: 32px;
  padding: 12px;
  box-sizing: border-box;
}
.index,
.text {
  flex: 1;
}
.text {
  max-width: 400px;
}
.index span {
  display: inline-block;
  width: 160px;
  text-align: right;
}
.Rheader {
  display: flex;
  width: 100%;
}
.Rtable-cell,
.Rtable-cellfull {
  box-sizing: border-box;
  flex-grow: 1;

  padding: 10px;
  overflow: hidden;
  list-style: none;
}
.Rtable-cell.thead{
  font-weight: 700;
}
.Rtable-cellfull {
  box-sizing: border-box;
  flex-grow: 1;

  padding: 10px;
  overflow: hidden;
  list-style: none;
  height: 100px;
  background-color: white;
}
.big {
  height: 200px;
  background-color: rgb(124, 124, 145);
}
.Rtable-cell > h1,
.Rtable-cell > h2,
.Rtable-cell > h3,
.Rtable-cell > h4,
.Rtable-cell > h5,
.Rtable-cell > h6 {
  margin: 0;
}
/* Table column sizing
================================== */
.Rtable--2cols .Rtable-cell {
  width: 50%;
}
.Rtable--3cols .Rtable-cell {
  width: 33.33%;
}
.Rtable--4cols .Rtable-cell {
  width: 25%;
}
.Rtable--5cols .Rtable-cell {
  width: 20%;
}
.Rtable--6cols .Rtable-cell {
  width: 16.6%;
}
.Rtable-cellfull {
  width: 100%;
}

.btn-container{
  width: 100;
  margin-bottom: 5vh;
  text-align: right;
  display: block;
}
</style>