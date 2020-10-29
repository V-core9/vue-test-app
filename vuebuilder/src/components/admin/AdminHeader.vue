<template>
  <div class="adminHeader">
    <AdminNavigation />
  </div>
</template>

<script>
import AdminNavigation from "@/components/layouts/AdminNavigation.vue";

export default {
  name: "AdminHeader",
  components: {
    AdminNavigation
    }
};
</script>

<style lang="scss" scoped>
.adminHeader {
  background: #333;
  display: flex;
}
</style>
