<template>
  <div class="inputBox">
    <input type="text" v-model="userTodoItem" @keyup.enter="inputData">
    <div class="addContainer">
      <i class="fa-solid fa-plus addBtn" @click="inputData"></i>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userTodoItem: ""
    }
  },
  methods: {
    inputData() {
      this.$emit("userinputdata", this.userTodoItem);
      this.userTodoItem = "";
    }
  }
}
</script>

<style scoped>
  input:focus {outline: none;}
  .inputBox {background: rgba(255, 255, 255, .3); display: flex; height: 50px; line-height: 50px; border-radius: 5px; box-shadow: 10px 10px 10px rgba(0, 0, 0, .3);}
  .inputBox input {padding-left: 10px; background-color: rgba(255, 255, 255, 1); width: calc(100% - 50px); border-style: none; border: 0; font-size: 0.9rem; color: #000;}
  .addContainer {float: right; background: #efefef; display: block; width: 50px; height: 100%; border-radius: 0 5px 5px 0; cursor: pointer;}
  i {color: #000;}
  .addBtn {cursor: pointer; color: #000; vertical-align: middle;}
  .closeModalBtn {color: #42b983;}
</style>