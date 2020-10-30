<template>
    <div class="singleTodo" v-bind:class="{'completedTodo':singleTodo.completed}" v-on:click="markCompleteSingle">
        <div class="infoSpace">
            <input type="checkbox" v-model="this.singleTodo.completed" v-on:change="markCompleteSingle"/>
            <p>{{singleTodo.title}}</p>
        </div>
        <button class="del" @click="this.sendForDelete">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["singleTodo"],
    methods: {
        markCompleteSingle() {
            this.singleTodo.completed = !this.singleTodo.completed;
        },
        sendForDelete(e) {
            e.stopPropagation();
            this.$emit('del-todo-single',this.singleTodo.id);
        }
    }
}
</script>

<style scoped>
    .singleTodo {
        background: #3c3c3c;
        padding: 5px 10px;
        display: flex;
        cursor: pointer;
        justify-content: space-between;
    }
    .infoSpace{
        display: flex;
        align-items: center;
        flex-direction: row;
        gap: .5em;
    }
    
    .singleTodo > lable > p {
        pointer-events: none;
    }
    
    .completedTodo {
        background: #2b2b2b;
        color: #3a5782;
    }
    
    .completedTodo .infoSpace p {
       text-decoration: line-through;
    }
    .singleTodo p{
        font-size: 1em;
    }
    .del {
        background: red;
        border: none;
        width: 1.5em;
        height: 1.5em;
        color: white;
    }
</style>