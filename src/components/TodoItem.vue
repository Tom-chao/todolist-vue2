<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="toItemValue.done"
        @change="itemChangeInput(toItemValue.id)"
      />
      <!-- <input type="checkbox" v-model="toItemValue.done" /> -->

      <span>{{ toItemValue.title }}</span>
    </label>
    <button class="btn btn-danger" @click="deleteListData(toItemValue.id)">
      删除
    </button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["toItemValue", "checkTodo", "deleteTodo"],
  data() {
    return {
      toItemValues: this.toItemValue,
    };
  },
  methods: {
    itemChangeInput(id) {
      this.checkTodo(id);
    },
    deleteListData(showItem) {
      if (confirm("Are you sure delete?")) {
        console.log(this.deleteTodo);
        this.deleteTodo(showItem);
      }
    },
  },
};
</script>

<style>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}
li label {
  float: left;
  cursor: pointer;
}
li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}
li button {
  float: right;
  display: none;
  margin-top: 3px;
}
li:before {
  content: initial;
}
li:last-child {
  border-bottom: none;
}
</style>
