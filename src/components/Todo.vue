<template>
  <section>
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem
        v-bind:todoItem="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
      />
    </div>
  </section>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todo",
  props: ["todos"],
  components: {
    TodoItem,
  },
};
</script>

<style lang="stylus" scoped></style>