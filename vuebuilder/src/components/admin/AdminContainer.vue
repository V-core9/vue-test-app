<template>
    <div class="adminContainer">
        <AdminHeader />
        <AdminInner />
        <AdminFooter />
    </div>
</template>

<script>
import AdminHeader from "@/components/admin/AdminHeader.vue";
import AdminInner from "@/components/admin/AdminInner.vue";
import AdminFooter from "@/components/admin/AdminFooter.vue";

export default {
  name: "AdminContainer",
  components: {
    AdminHeader, AdminInner, AdminFooter,
  },
  data() {
    return {
      adminConfig: {
        templateLayout : "default",
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.adminContainer {
  color: #444;
}

</style>