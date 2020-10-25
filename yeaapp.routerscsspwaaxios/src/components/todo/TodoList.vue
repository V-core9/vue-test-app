<template>
    <div class="todoList">
        <div class="singleItem" v-bind:key="single.id" v-for="single in todoList">
            <TodoItem v-bind:singleTodo="single" v-on:del-todo-single="$emit('del-todo-single', single.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    name: "TodoList",
    components: {
        TodoItem,
    },
    props: ["todoList"]
}
</script>

<style scoped>
    .todoList {
        padding: 5px;
        background: rgba(255,255,255,0.1);
    }
    
    h3{
        margin-bottom: 10px;
    }

    .singleItem{
        transition: 0.25s ease all;
        box-shadow: 0 0 0 black;
    }
    
    .singleItem:hover {
        transition: 0.35s ease all;
        box-shadow: 0 5px 10px black;
        z-index: 10;
        position: relative;
    }
    
</style>