<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  name: "MainApplication",
  components: {}
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}

#app {
  font-size: 18.5px;
  font-family: monospace;
  color: #2c3e50;
  min-height: 100vh;
  display: flex;
  width: 100%;
  position: relative;
}

#nav {
  padding: 10px 20px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
