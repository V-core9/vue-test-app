<template>
  <div class="adminPage">
    <AdminContainer />
  </div>
</template>

<script>
// @ is an alias to /src
import AdminContainer from "@/components/admin/AdminContainer.vue";

export default {
  name: "AdminPage",
  components: {
    AdminContainer
  }
};
</script>

<style lang="scss" scoped>
.adminPage {
    background: orange;
    flex: 1;
}
</style>

