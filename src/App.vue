<template>
  <div id="app">
    <Header/>

    <router-view/>
  </div>
</template>

<script>
import Header from "./components/layout/Header";

export default {
  name: "App",
  components: {
    Header
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      // this.todos = this.todos.filter(todo => todo.id !== id);
      fetch(`https://jsonplaceholder.typicode.com/todos/${id}`, {
        method: "DELETE"
      })
        .then(response => response.json())
        .then(data => (this.todos = this.todos.filter(todo => todo.id !== id)));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      fetch("https://jsonplaceholder.typicode.com/todos/", {
        method: "post",
        body: JSON.stringify({ title: title, completed: completed }),
        headers: {
          "Content-type": "application/json; charset=UTF-8"
        }
      })
        .then(response => response.json())
        .then(data => (this.todos = [...this.todos, data]))
        .catch(err => console.log(err));
      // this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    //get from jsonplaceholder api
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=5/")
      .then(result => result.json())
      .then(data => (this.todos = data));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>

