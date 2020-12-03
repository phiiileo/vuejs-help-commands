<template>
  <AddTodo v-on:add-todo="addTodo" />
  <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo" />
</template>

<script>
import Todo from "./components/Todo";
import AddTodo from "./components/AddTodo";
import axios from "axios";
export default {
  name: "App",
  components: {
    Todo,
    AddTodo,
  },
  methods: {
    addTodo(todo) {
      const { title, completed } = todo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => {
          this.todos.push(res.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    deleteTodo(id) {
      axios
        .delete("https://jsonplaceholder.typicode.com/todos/" + id)
        .then((res) => {
          console.log(res)
          this.todos = this.todos.filter((todo) => todo.id !== id);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  data() {
    return {
      todos: [
        { id: 1, title: "Start learning vue" },
        { id: 2, title: "Search for resource to use" },
        { id: 3, title: "Get a youtube link", completed: true },
        { id: 4, title: "Start learning" },
        { id: 5, title: "Create a test project" },
        { id: 6, title: "Start coding" },
      ],
    };
  },
  created() {
    console.log(123456789);
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then((res) => {
        console.log((this.todos = res?.data));
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
