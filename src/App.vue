<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @click:addTodoItem="addOneItem"></TodoInput>
    <TodoList :propsdata="items"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue"
import TodoInput from "./components/TodoInput.vue"
import TodoList from "./components/TodoList.vue"
import TodoFooter from "./components/TodoFooter.vue"




export default {
  data () {
    return {
      items: []
    }
  },
  methods: {
    addOneItem(todoItem){
      //처음부터 문자열로 할당하고, parse를 사용할 수 있는지
      var obj = {
        completed: false, items: todoItem
      };

      // key값과 value값을 동일하게 해주는 작업
      localStorage.setItem(todoItem, JSON.stringify(obj)); // 값이 문자열로 반환
      this.items.push(obj);
    }
  },
  created() {
    if (localStorage.length > 0) {
      for(var i = 0; i< localStorage.length; i++){
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          localStorage.getItem(localStorage.key(i));
          //로컬 스토리지의 getItem() 메서드는 keyName을 인자로 keyValue를 리턴해 준다.
          this.items.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
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
  body {margin: 0 auto; text-align: center; background-color: #f6f6f6;}
  input {border-style: groove; width: 200px;}
  button {border-style: groove;}
  .shadow {box-shadow: 5px 10px 10px rgba(0, 0, 0, .09);}
</style>
