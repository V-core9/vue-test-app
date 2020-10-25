<template>
  <div id="app">
    <TodoList v-bind:todoList="todoList" v-on:del-todo-single="deleteSingleTodo"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      todoList: [
        {
          id: 1,
          title: "todo first thing",
          completed: false
        },
        {
          id: 2,
          title: "miki has a thing",
          completed: true
        },
        {
          id: 3,
          title: "todo yeaaa thing",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteSingleTodo(id){
      this.todoList = this.todoList.filter(single => single.id !== id);
    }
  }
}
</script>

<style>

  * {
    padding: 0;
    margin: 0;
  }
  
  body {
    font-family: monospace;
    font-size: 16px;
    background: #333;
    color: #f0f0f0;
  }

</style>
