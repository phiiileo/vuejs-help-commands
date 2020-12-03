<template>
  <AddTodo v-on:add-todo="addTodo" />
  <Todo v-bind:todos="todos" v-on:del-todo="deleteTodo" />
</template>

<script>
import Todo from "./components/Todo";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: {
    Todo,
    AddTodo
  },
  methods: {
    addTodo(todo){
      console.log(todo)
      this.todos.push(todo)
    },
    deleteTodo(id) {
      console.log(id);
      this.todos = this.todos.filter((todo) => todo.id !== id);
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
