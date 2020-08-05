<template>
  <div v-bind:class="{ 'is-complete': item.completed }" class="todo-item">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{ item.title }}
      <button class="del" @click="$emit('del-item', item.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    item: Object,
  },
  methods: {
    markComplete() {
      this.item.completed = !this.item.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
