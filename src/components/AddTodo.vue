<template>
  <div>
    <form @submit="handleSubmit">
      <input type="text" name="title" v-model="title" placeholder="Add Todo..." />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
import uuid from "../utils/uuid";

export default {
  name: "AddTodo",
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      if (this.title === "") return;

      const newTodo = {
        id: uuid(),
        title: this.title,
        completed: false,
      };

      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
  data() {
    return {
      title: "",
    };
  },
};
</script>

<style scoped>
form {
  margin: 1em;
  text-align: center;
}

input {
  padding: 0.7em;
  margin-right: 1em;
  border-radius: 6px;
  border: none;
}

button {
  padding: 0.7em;
  background-color: #08a4ff;
  color: #fff;
  border-radius: 6px;
  border: none;
}
</style>