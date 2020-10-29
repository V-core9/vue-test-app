<template>
  <div class="adminHeader">
      <div class="logoOwner">
          <img src="../../assets/bls-logo.png">
          <p>Xadmin</p>
      </div>
      <div class="headerInner">
        <div class="headerOptions">
            <AdminNavigation />
        </div>
        <div class="userData">
            <AdminNavigation />
        </div>
      </div>
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
    background: #1976d2;
    color: #f0f0f0;
    display: flex;
    align-items: center;
    gap: 1em;

    .logoOwner {
        display: flex;
        flex-direction: row;
        align-items: center;
        background: white; 
        padding: 7.5px 15px;
        min-width: 280px;

        img {
            max-height: 45px;
            filter: grayscale(1) brightness(6);
        }

        p {
            color: #555555;
            font-size: 1.75em;
            font-weight: bold;
        }
    }

    .headerInner {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        flex: 1;
    }
}
</style>
