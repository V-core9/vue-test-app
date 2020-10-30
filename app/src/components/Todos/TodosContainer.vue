<template>
  <div id="todosContainer">
    <TodosList v-bind:todoList="todoList" v-on:del-todo-single="deleteSingleTodo"/>
    <TodoItemAdd v-on:add-todo-item="TodoItemAdd"/>
  </div>
</template>

<script>
import TodosList from './TodosList.vue'
import TodoItemAdd from './TodoItemAdd.vue'
import axios from 'axios';
export default {
    name: 'TodosContainer',
    components: {
        TodosList,
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