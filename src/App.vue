<template>
  <div class="content">
    <Todo />
  </div>
</template>

<script>
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: {
    Todo
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

body {
  background-color: #118ab2;
  color: #0d0d0d;
  font-family: 'Montserrat', sans-serif !important;
  font-weight: 500;
}
</style>
