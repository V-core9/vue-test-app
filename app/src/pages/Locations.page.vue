<template>
  <div class="locationsPage page">
    <LocationsContainer/>
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>
// @ is an alias to /src
import LocationsContainer from '@/components/Locations/LocationsContainer.vue'

export default {
  name: 'LocationsPage',
  components: {
    LocationsContainer
  }
}
</script>