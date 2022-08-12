<template>
  <div class="todo-footer" v-if="total">
    <label>
      <!-- <input type="checkbox" :checked="isAll" @change="checkAll" /> -->
      <input type="checkbox" v-model="isAll" />
    </label>
    <span>
      <span>已完成{{ doneTotal }}</span> / 全部{{ todoList.length }}
    </span>
    <button class="btn btn-danger" @click="deleteListData">
      清除已完成任务
    </button>
  </div>
</template>

<script>
export default {
  name: "TodoFooter",
  props: ["checkTodo", "todoList", "checkAllTodo", "deleteAllData"],
  data() {
    return {};
  },
  computed: {
    total() {
      return this.todoList.length;
    },
    doneTotal() {
      // let i = 0;
      // this.todoList.forEach((todo) => {
      //   if (todo.done) i++;
      // });
      // return i;
      return this.todoList.reduce((pre, todo) => {
        return pre + (todo.done ? 1 : 0);
      }, 0);
    },
    isAll: {
      get() {
        return this.doneTotal === this.total && this.total > 0;
      },
      set(value) {
        this.checkAllTodo(value);
      },
    },
  },
  methods: {
    deleteListData() {
      if (confirm("Are you sure deteleAll?")) {
        this.deleteAllData();
      }
    },
  },
};
</script>

<style>
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
