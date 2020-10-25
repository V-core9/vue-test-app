<template>
    <form @submit="addTodoItem">
        <input type="text" v-model="title" name="title" placeholder="Add some todo....">
        <input type="submit" value="Add to list" class="appBtn">
    </form>
</template>

<script>
export default {
    name: "TodoItemAdd",
    data() {
        return {
            title: "",
        }
    },
    methods: {
        addTodoItem(e){
            e.preventDefault();
            const newTodoItem = {
                id: "",
                title: this.title,
                completed: false,
            }

            this.$emit('add-todo-item', newTodoItem);
        }
    }
}
</script>

<style scoped>

    input[type="text"] {
        padding: 0.25em 0.5em;
        margin: 0.25em;
        background: #2b2b2b;
        border: none;
        color: white;
        border-bottom: 2px solid transparent;
        transition: 0.25s ease all;
    }

    input[type="text"]::placeholder {
        color: black;
    }

    input[type="text"]:focus {
        outline: none;
        border-bottom: 2px solid orange;
    }

    input[type="text"]:hover {
        border-bottom: 2px solid #03A9F4;
        box-shadow: 0 2.5px 10px black;
        cursor: auto;
    }
</style>