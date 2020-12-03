
<template>
  <section>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add todo..."
      />
      <button>Submit</button>
    </form>
  </section>
</template>

<script>
import * as uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      if (this.title === "") return;
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        compeleted: false,
      };
      console.log(newTodo);
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>
<style scoped>
</style>