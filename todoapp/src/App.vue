<template>
  <div id="app">
    <Header headerTitle="Todo List Title"/>
    <TodoList v-bind:todoList="todoList" v-on:del-todo-single="deleteSingleTodo"/>
    <TodoItemAdd v-on:add-todo-item="TodoItemAdd"/>
  </div>
</template>

<script>
import Header from './components/layout/Header.vue';
import TodoList from './components/TodoList.vue'
import TodoItemAdd from './components/TodoItemAdd.vue'

export default {
  name: 'App',
  components: {
    Header,
    TodoList,
    TodoItemAdd,
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
    },
    TodoItemAdd(newTodoItem){
      newTodoItem.id = (this.todoList.length + 1);
      this.todoList = [...this.todoList, newTodoItem];
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

  #app {
    margin: 10px;
    background: #444;
  }
</style>
