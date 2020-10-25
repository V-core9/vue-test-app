<template>
  <div class="home">
    <Hero 
        title="Welcome to Your App"
        subtitle="You can do many things when you find will."
        button="More Info" 
        url="/about" 
        backImg="../img/back.jpg"
        />
    <HelloWorld msg="Welcome to Your App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Hero from '@/components/pageModules/Hero.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Hero
  }
}
</script>
