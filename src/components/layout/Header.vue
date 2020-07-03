<template>
  <div class="header">
    <h1>Todo List</h1>
    <router-link to="/">Go to Home</router-link>|
    <router-link to="/about">Go to About</router-link>
  </div>
</template>
<script>
export default {
  name: "Header"
};
</script>
<style scoped>
.header {
  background: black;
  color: whitesmoke;
}
.header a {
  color: whitesmoke;
  text-decoration: none;
  margin: 5px 10px;
}
</style>

