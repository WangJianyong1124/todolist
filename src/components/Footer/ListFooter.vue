<template>
  <div class="todo-footer" v-if="total > 0">
    <label>
      <input type="checkbox" :checked="isAllCheck" @click="checkAllIPL"/>
    </label>
    <span>
      <span>已完成 {{ successful }}</span> / 全部 {{ total }}
    </span>
    <button class="btn btn-danger" v-on:click="clearAllIPL">清除已完成任务</button>
  </div>
  <div v-else>
    <h1>还没有制定任务哦 赶紧添加吧!!!</h1>
  </div>
</template>

<script>
export default {
  name: "ListFooter",
  props: ["todos", "checkAll", "clearAll"],
  computed: {
    successful() {
      return this.todos.reduce(
        (pre, current) => pre + (current.isDone ? 1 : 0),
        0
      );
    },
    total() {
      return this.todos.length;
    },
    isAllCheck() {
      if (this.successful === this.total) {
        return 1;
      }
      return 0
    },
  },
  methods: {
    checkAllIPL(e){
     this.checkAll(e.target.checked);
    },

    clearAllIPL(){
      this.clearAll()
    }
  }
};
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>