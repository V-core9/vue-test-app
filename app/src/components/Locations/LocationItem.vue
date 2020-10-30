<template>
    <div class="singleLocation" v-bind:class="{'completedLocation':singleLocation.completed}" v-on:click="markCompleteSingle">
        <div class="infoSpace">
            <input type="checkbox" v-model="this.singleLocation.completed" v-on:change="markCompleteSingle"/>
            <p>{{singleLocation.title}}</p>
        </div>
        <button class="del" @click="this.sendForDelete">x</button>
    </div>
</template>

<script>
export default {
    name: "LocationItem",
    props: ["singleLocation"],
    methods: {
        markCompleteSingle() {
            this.singleLocation.completed = !this.singleLocation.completed;
        },
        sendForDelete(e) {
            e.stopPropagation();
            this.$emit('del-location-single',this.singleLocation.id);
        }
    }
}
</script>

<style scoped>
    .singleLocation {
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
    
    .singleLocation > lable > p {
        pointer-events: none;
    }
    
    .completedLocation {
        background: #2b2b2b;
        color: #3a5782;
    }
    
    .completedLocation .infoSpace p {
       text-decoration: line-through;
    }
    .singleLocation p{
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