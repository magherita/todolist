<template>
  <div>
    <AddTodoItem v-on:add-todo-item="addTodoItem" />

    <TodoList v-bind:items="todoItems" v-on:del-item="deleteItem" />
  </div>
</template>

<script>
import TodoList from "../components/TodoList.vue";
import AddTodoItem from "../components/AddTodoItem.vue";

import axios from "axios";

export default {
  name: "Home",
  components: {
    TodoList,
    AddTodoItem,
  },
  data() {
    return {
      todoItems: [],
    };
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((response) => {
        this.todoItems = response.data;
      })
      .catch((err) => console.log(err));
  },
  methods: {
    deleteItem(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => {
          this.todoItems = this.todoItems.filter((item) => item.id !== id);
        })
        .catch((err) => console.log(err));
    },
    addTodoItem(todoItem) {
      const { title, completed } = todoItem;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((response) => {
          this.todoItems = [...this.todoItems, response.data];
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>
