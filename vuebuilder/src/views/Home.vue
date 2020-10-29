<template>
  <div class="home">
    <AppNavigation />
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import AppNavigation from "@/components/layouts/AppNavigation.vue";
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomePage",
  components: {
    HelloWorld,
    AppNavigation
  }
};
</script>
