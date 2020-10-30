<template>
    <div class="locationsList">
        <div class="singleItem" v-bind:key="single.id" v-for="single in locationList">
            <LocationItem v-bind:singleLocation="single" v-on:del-location-single="$emit('del-location-single', single.id)" />
        </div>
    </div>
</template>

<script>
import LocationItem from './LocationItem.vue';
export default {
    name: "LocationsList",
    components: {
        LocationItem,
    },
    props: ["locationList"]
}
</script>

<style scoped>
    .locationsList {
        padding: 5px;
        background: rgba(255,255,255,0.1);
    }
    
    h3{
        margin-bottom: 10px;
    }
    .singleItem{
        transition: 0.25s ease all;
        box-shadow: 0 0 0 black;
        color: white;
    }
    
    .singleItem:hover {
        transition: 0.35s ease all;
        box-shadow: 0 5px 10px black;
        z-index: 10;
        position: relative;
    }
    
</style>