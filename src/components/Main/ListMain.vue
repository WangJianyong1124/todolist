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
// 随机生成id
import { nanoid } from "nanoid";

export default {
  name: "ListMain",
  data() {
    return {
      todos: [
        { id: nanoid(), title: "吃饭", isDone: false },
        { id: nanoid(), title: "睡觉", isDone: true },
        { id: nanoid(), title: "打豆豆", isDone: false },
      ],
    };
  },
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