<template>
  <div id="navAdmin">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/admin">Admin</router-link>
  </div>
</template>

<script>
export default {
  name: "AdminNavigation",
  components: {}
};
</script>

<style scoped>
#navAdmin {
    display: flex;
    flex-direction: row;
}
</style>