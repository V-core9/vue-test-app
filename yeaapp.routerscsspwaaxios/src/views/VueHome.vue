<template>
  <div class="vuehome">
    <img alt="Vue logo" src="../assets/vue-logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App Page."/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'VueHome',
  components: {
    HelloWorld
  }
}
</script>
