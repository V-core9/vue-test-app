<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <TodoContainer/>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoContainer from '@/components/todo/Todo.vue'

export default {
  name: 'Todo',
  components: {
    TodoContainer
  }
}
</script>
