<template>
  <section>
    <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
     <input type="checkbox"  v-on:change="markComplete"> 
     {{ todoItem.title }}
     <button v-on:click="$emit('del-todo', todoItem.id)">x</button>
    </div>
  </section>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoItem"],
  data (){
      return{
          todo: this.todoItem
      }
  },
  methods:{
      markComplete(){
          this.todo.comleted = true
      }
  }
};
</script>
<style scoped>
.todo-item {
    background-color :grey;
    color: white;
    padding: 1rem 2rem
}

.is-completed{
    background-color: green;
    text-decoration: line-through;
}
</style>