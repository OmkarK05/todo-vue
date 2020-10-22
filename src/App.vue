<template>
  <div>
    <h1>Hello from Youtube</h1>
    <TodoList></TodoList>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList,
  },
};
</script>

<style>
body {
  background-color: rgb(66, 60, 60);
  color: aliceblue;
}
</style>
