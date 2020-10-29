<template>
  <div class="adminSidebar">
    <AppNavigation />
  </div>
</template>

<script>
import AppNavigation from "@/components/layouts/AppNavigation.vue";

export default {
  name: "AdminSidebar",
  components: {
    AppNavigation
    }
};
</script>

<style lang="scss" scoped>
.adminSidebar {
  background: #333;
  display: flex;
  flex-direction: column;
  #nav {
    display: flex;
    flex-direction: column;
  }
}
.topSidebar {

    #nav{
        flex-direction: row;
    }
}
</style>
