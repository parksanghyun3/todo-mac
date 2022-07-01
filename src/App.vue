<template>
  <div id="app">
    <TodoHeader></TodoHeader> 
    <TodoInput v-on:userinputdata="addInputData"></TodoInput> <!-- 여기에서 bind인지 on인지 제대로 확인하기-->
    <TodoList v-bind:propsdata="listItem"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>

import TodoHeader from "./components/TodoHeader.vue"
import TodoInput from "./components/TodoInput.vue"
import TodoList from "./components/TodoList.vue"
import TodoFooter from "./components/TodoFooter.vue"




export default {
  data() {
    return {
      listItem: []
    }
  },
  methods: {
    addInputData(newItem) {
      var obj = {
        item: newItem 
      }
      localStorage.setItem(newItem, JSON.stringify(obj));
      this.listItem.push(JSON.parse(localStorage.getItem(newItem)));
    },
  },
  components: {
    "TodoHeader": TodoHeader,
    "TodoInput": TodoInput,
    "TodoList": TodoList,
    "TodoFooter": TodoFooter,
  }
}
</script>

<style>
  body {margin: 0 auto; text-align: center; background-color: #f6f6f6; width: 400px;}
  input {border-style: groove; width: 200px;}
  button {border-style: groove;}
  .shadow {box-shadow: 5px 10px 10px rgba(0, 0, 0, .09);}
</style>
