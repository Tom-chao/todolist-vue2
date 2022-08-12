<template>
  <div class="todo-header">
    <input
      type="text"
      placeholder="请输入你的任务名称，按回车键确认"
      v-model="title"
      @keyup.enter="addItemData"
    />
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: "TodoHeader",
  props: ["receiveData"],
  data() {
    return { title: "" };
  },
  methods: {
    addItemData(event) {
      //将用户的输入包装成一个对象
      this.title = event.target.value;
      if (!this.title) {
        return alert("输入不能为空");
      }

      const todoObj = { id: nanoid(), title: this.title, done: false };
      this.receiveData(todoObj);
      //   添加完成之后清楚输入框
      this.title = "";
    },
  },
};
</script>

<style>
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}
.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
