<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <ListHeader :add="addItem" />
        <ListMain
          :todos="todos"
          :checkToggle="checkToggle"
          :deleteItem="deleteItem"
        />
        <ListFooter :todos="todos" :checkAll="checkAll" :clearAll="clearAll"/>
      </div>
    </div>
  </div>
</template>

<script>
// 导入Header组件
import ListHeader from "./components/Header/ListHeader";
// 导入ListMain组件
import ListMain from "./components/Main/ListMain";
// 导入ListFooter组件
import ListFooter from "./components/Footer/ListFooter";
// 随机生成id
import { nanoid } from "nanoid";

export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: nanoid(), title: "吃饭", isDone: false },
        { id: nanoid(), title: "睡觉", isDone: true },
        { id: nanoid(), title: "打豆豆", isDone: false },
      ],
    };
  },
  methods: {
    // 增加待做项
    addItem(title) {
      // 保存新数据
      const newData = { id: nanoid(), title: title, isDone: false };
      // 将新数据添加到todos中
      this.todos.unshift(newData);
    },

    // 勾选/取消勾选待做项
    checkToggle(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) {
          todo.isDone = !todo.isDone;
        }
      });
    },

    // 删除待做项
    deleteItem(id) {
      if (confirm("确定删除嘛?")) {
        this.todos = this.todos.filter((todo) => {
          return todo.id !== id;
        });
      }
    },

    // 全选
    checkAll(isCheck) {
      this.todos.forEach((todo) => {
        if (isCheck) {
          todo.isDone = true;
        } else {
          todo.isDone = false;
        }
      });
    },

    // 删除全部
    clearAll(){
      this.todos = []
    }
  },
  components: {
    ListHeader,
    ListMain,
    ListFooter,
  },
};
</script>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2),
    0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
