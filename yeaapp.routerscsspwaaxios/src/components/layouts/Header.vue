<template>
    <header class="header">
        <h1>{{headerTitle}}</h1>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        headerTitle: String
    }
}
</script>

<style scoped>
    .header h1 {
        font-size: 1.5em;
        font-weight: 500;
        color: #03A9F4;
    }
</style>