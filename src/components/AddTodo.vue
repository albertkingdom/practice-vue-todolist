<template>
  <div>
    <form v-on:submit="addtodo">
      <input type="text" name="title" v-model="title" placeholder="Add todo...">
      <input type="submit" value="Submit">
    </form>
  </div>
</template>
<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addtodo(e) {
      e.preventDefault();
      // console.log("new todo");
      // console.log(this.title)
      const newTodo = {
        // id: uuidv4(),//RESTful api會自動編號
        title: this.title,
        completed: false
      };
      //send up to parents
      this.$emit("add-todo", newTodo);
      //clean input content
      this.title = "";
    }
  }
};
</script>
<style scoped>
form {
  display: flex;
  justify-content: center;
}
input[type="submit"] {
  background-color: brown;
  border: none;
  border-radius: none;
  color: white;
  font-size: 18px;
  padding: 5px 8px;
}
</style>


