<template>
  <div id="app">
    <h1>My little to do list</h1>
    <hr />
    <todo-list />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
export default {
  name: "app",
  components: {
    TodoList
  }
};
</script>

<style scoped>
  #app {
    text-align: center;
  }
</style>