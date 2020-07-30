<template>
  <div id="TodoList">
    <TodoItem
      :key="todo.id"
      :todo="todo"
      v-for="todo in todos"
      v-on:del-todo="$emit('del-todo', todo.id)"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "TodoList",
  props: {
    todos: {
      type: Array,
      required: true
    }
  },
  components: {
    TodoItem,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#TodoList {
  max-width: 900px;
  width: 60%;
  margin: 1em auto;
}

h1 {
  text-align: center;
}
</style>
