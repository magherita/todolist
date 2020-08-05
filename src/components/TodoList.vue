<template>
  <div>
    <div v-bind:key="item.id" v-for="item in items">
      <TodoItem v-bind:item="item" v-on:del-item="$emit('del-item', item.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "TodoList",
  props: {
    items: Array,
  },
  components: { TodoItem },
};
</script>

<style scoped></style>