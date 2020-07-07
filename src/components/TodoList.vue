<template>
  <div class="container">
    <div class="search-wrap">
      <input type="text" class="search" v-model="keyword">
    </div>
    <div class="section">
      <div class="section-content">
        <div class="section-title">Methods</div>
        <div class="section-desc">got to have em</div>
      </div>
      <div class="section-action">
        <span @click="addItem">+</span>
      </div>
    </div>
    <div class="list">
      <div v-for="(item,index) in list" :key="item.uuid"  class="list-item">
        <div class="list-item-left">
          <div class="list-item-title">Task</div>
          <div class="list-item-index">{{ index + 1 }}</div>
        </div>
        <div class="list-item-text">{{ item.text }}</div>
        <div class="list-item-delete" @click="deleteItem(item.uuid)">x</div>
      </div>
    </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: 'TodoList',
  data () {
    return {
      keyword: '',
      sourceList: [
        { uuid: '123333', text: 'item 1 placeholder' },
        { uuid: '123334', text: 'test 2 placeholder' },
        { uuid: '123332', text: 'test 3 placeholder' }
      ],
    }
  },
  computed: {
    list () {
      return this.keyword ? this.sourceList.filter(item => item.text.indexOf(this.keyword) > -1) : this.sourceList
    }
  },
  methods: {
    addItem () {
      this.sourceList.push({
        uuid: uuidv4(),
        text: `item ${this.sourceList.length + 1} placeholder`
      })
    },
    deleteItem (uuid) {
      this.sourceList = this.sourceList.filter(item => item.uuid !== uuid)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .container{
    max-width: 900px;
    height: 100%;
    margin: 0 auto;
    background-color: #FFFFFF;
    padding: 20px;
  }
  .search-wrap{
    display: flex;
    justify-content: flex-end;
    margin-bottom: 10px;
  }
  .search-wrap input {
    line-height: 20px;
  }
  .section{
    border-top: 2px solid gray;
    border-bottom: 2px solid gray;
    padding: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .section-title{
    font-size: 18px;
    font-weight: bold;
  }
  .section-desc{
    font-size: 14px;
  }
  .section-action span{
    display: block;
    width: 30px;
    height: 30px;
    border: 2px solid blue;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 20px;
    cursor: pointer;
    font-weight: bold;
    color: blue;
  }
  .list{
    padding: 10px 0;
  }
  .list-item{
    display: flex;
    width: 50%;
    align-items: center;
    justify-content: space-between;
    border-radius: 5px;
    border: 1px solid gray;
    margin-bottom: 10px;
    padding: 6px 10px;
  }
  .list-item-left{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-right: 10px;
  }
  .list-item-title{
    font-size: 16px;
    color: blue;
  }
  .list-item-index{
    display: block;
    width: 18px;
    height: 18px;
    border: 2px solid red;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 14px;
    cursor: pointer;
    font-weight: bold;
    color: red;
  }
  .list-item-delete{
    display: flex;
    align-items: center;
    justify-content: center;
    margin-left: 10px;
    width: 20px;
    height: 20px;
    line-height: 20px;
    background-color: gray;
    color: white;
    border-radius: 50%;
    font-size: 14px;
    cursor: pointer;
  }
</style>
