<template>
  <div id="todoContainer">
    <Header headerTitle="Todo List Title"/>
    <TodoList v-bind:todoList="todoList" v-on:del-todo-single="deleteSingleTodo"/>
    <TodoItemAdd v-on:add-todo-item="TodoItemAdd"/>
  </div>
</template>

<script>
import Header from '../layouts/Header.vue';
import TodoList from './TodoList.vue'
import TodoItemAdd from './TodoItemAdd.vue'
import axios from 'axios';

export default {
    name: 'TodoContainer',
    components: {
        Header,
        TodoList,
        TodoItemAdd,
    },
    data() {
        return {
        todoList: []
        }
    },
    methods: {
        deleteSingleTodo(id){
            axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                .then(res => { this.todoList = this.todoList.filter(single => single.id !== id); console.log(res)})
                .catch(error => console.log(error));
           
        },
        TodoItemAdd(newTodoItem){
            const { title, completed } = newTodoItem;

            axios.post('https://jsonplaceholder.typicode.com/todos',{
                title,
                completed
            })
                .then(res =>this.todoList = [...this.todoList, res.data] )
                .catch(error => console.log(error));
        }
    },
    created() {
        axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
            .then( res => this.todoList = res.data )
            .catch( error => console.log(error) );
    }
}
</script>

<style scoped>

  #todo {
    margin: 10px;
    background: #444;
  }
</style>
