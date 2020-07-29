<template>
  <div class="todo" v-bind:class="{'completed' : todo.completed}">
    <p>
      <input type="checkbox" v-on:change="toggleComplete" v-bind:checked="todo.completed" />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="delete">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    toggleComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo {
  margin: 1em;
  padding: 1em;
  border-bottom: 1px dashed #333;
}

.completed {
  text-decoration: line-through;
  color: #888;
  background-color: #eee;
}

.delete {
  margin-left: 1em;
  padding: 0.5em 0.8em;
  background-color: tomato;
  border: none;
  border-radius: 6px;
  color: #fff;
}

input {
  margin-right: 1em;
}
</style>