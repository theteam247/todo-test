<template>
  <div id="app">
    <TodoList/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
html, body{
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
  background-color: #F8F8F8;
}
</style>
