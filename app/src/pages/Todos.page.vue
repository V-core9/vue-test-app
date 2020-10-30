<template>
  <div class="home">
    <TodosContainer/>
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import TodosContainer from '@/components/Todos/TodosContainer.vue'

export default {
  name: 'TodosPage',
  components: {
    TodosContainer
  }
}
</script>