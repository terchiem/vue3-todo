<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <TodoList v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from "./components/layout/Header";
import TodoList from "./components/TodoList";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: {
    Header,
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => this.todos = this.todos.filter((todo) => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      axios.post('https://jsonplaceholder.typicode.com/todos', newTodo)
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    },
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
};
</script>

<style>
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #eee;
}
</style>
