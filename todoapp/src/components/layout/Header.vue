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
        margin-bottom: 0.25em;
    }
</style>