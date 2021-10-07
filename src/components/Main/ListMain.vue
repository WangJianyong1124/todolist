<template>
  <div>
    <ul class="todo-main">
      <ListItem :todos="todos" />
    </ul>
  </div>
</template>

<script>
// 导入子组件Item
import ListItem from "./child/ListItem.vue";

export default {
  name: "ListMain",
  props: ["todos"],
  components: {
    ListItem,
  },
};
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>