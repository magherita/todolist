<template>
  <div>
    <form @submit.prevent="addTodoItem">
      <input
        type="text"
        name="title"
        placeholder="Add Todo..."
        v-model="todoItem.title"
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuid } from "uuid";

export default {
  name: "AddTodoItem",
  data() {
    return {
      todoItem: {
        id: null,
        title: "",
        completed: false,
      },
    };
  },
  methods: {
    addTodoItem() {
      const todoItem = {
        id: uuid(),
        title: this.todoItem.title,
        completed: this.todoItem.completed,
      };

      // emit submission event to parent component
      this.$emit("add-todo-item", todoItem);

      this.todoItem.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>
