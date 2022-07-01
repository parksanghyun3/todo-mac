<template>
  <div>
    <ul>
      <li v-for="todoitem in propsdata" v-bind:key="todoitem.item">
        <span>
          {{ todoitem.item }}
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  props: ["propsdata"],
}
</script>

<style scoped>
  ul {list-style-type: none; padding-left: 0px; margin-top: 0; text-align: left;}
  li {display: flex; align-items: center; min-height: 50px; height: 50px; margin: 0.5rem 0; padding: 0 0.9rem; background: #fff; border-radius: 5px;}
  li span {width: 100%;}
  .checkBtn {color: #62acde; margin-right: 5px; cursor: pointer;}
  .removeBtn {text-align: right; color : #de4343; cursor: pointer;}
  .checkBtnCompleted {color : #b3adad;}
  .textCompleted {color: #b3adad;}
  /* 리스트 아이템 트랜지션 효과 */
  .list-enter-active, .list-leave-active {transition: all 1s;}
  .list-enter, list-leave-to {opacity: 0; transform: translateY(30px);}
</style>