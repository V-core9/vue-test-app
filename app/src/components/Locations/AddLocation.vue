<template>
    <form @submit="addLocation">
        <input type="text" v-model="category" name="category" placeholder="Add some location category....">
        <input type="text" v-model="title" name="title" placeholder="Add some location title....">
        <input type="text" v-model="folder" name="folder" placeholder="Add some location folder....">
        <input type="text" v-model="img" name="img" placeholder="Add some location img....">
        <input type="text" v-model="start" name="start" placeholder="Add some location start....">
        <input type="text" v-model="end" name="end" placeholder="Add some location end....">
        <input type="text" v-model="date_taken" name="date_taken" placeholder="Add some location date_taken....">
        <input type="submit" value="Add to list" class="appBtn">
    </form>
</template>

<script>
export default {
    name: "AddLocation",
    data() {
        return {
            category: "",
            title: "",
            folder: "",
            img: "",
            start: "",
            end: "",
            date_taken: "",
        }
    },
    methods: {
        addLocation(e){
            e.preventDefault();
            const newLocationItem = {
                category: this.category,
                title: this.title,
                folder: this.folder,
                img: this.img,
                start: this.start,
                end: this.end,
                date_taken: this.date_taken
            }
            this.$emit('add-location-item', newLocationItem);
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
        color: #cacaca;
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