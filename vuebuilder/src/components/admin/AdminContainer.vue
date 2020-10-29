<template>
  <div class="adminContainer" v-bind:class="templateLayout">
    <AdminHeader />
    <div class="adminPageContent">
      <component :is="componentLeft" v-on:set-right-sidebar="setRightSidebar" />
      <component :is="componentRight" v-on:set-right-sidebar="setRightSidebar" />
    </div>
    <AdminFooter v-on:set-admin-template="setAdminTemplate" />
  </div>
</template>

<script>
import CookieHelper from "@/components/helpers/CookieHelper.js";
import AdminHeader from "@/components/admin/AdminHeader.vue";
import AdminInner from "@/components/admin/AdminInner.vue";
import AdminSidebar from "@/components/admin/AdminSidebar.vue";
import AdminFooter from "@/components/admin/AdminFooter.vue";

export default {
  name: "AdminContainer",
  components: {
    AdminHeader,
    AdminInner,
    AdminSidebar,
    AdminFooter
  },
  data() {
    return {
      templateLayout: null,
      componentLeft: null,
      componentRight: null
    };
  },
  methods: {
    setAdminTemplate: function(tempName) {
      switch (tempName) {
        case "rightSidebar":
          this.setRightSidebar();
          break;
        case "topSidebar":
          this.setTopSidebar();
          break;
        default:
          this.setDefaultOrder();
      }
    },
    setDefaultOrder: function() {
      console.log("Setting Default Template!");
      this.componentLeft = "AdminSidebar";
      this.componentRight = "AdminInner";
      this.templateLayout = "default";
      CookieHelper.setCookie('adminTemplate', 'default', 30);
    },
    setRightSidebar: function() {
      console.log("Setting RightSidebar Template!");
      this.componentLeft = "AdminInner";
      this.componentRight = "AdminSidebar";
      this.templateLayout = "rightSidebar";
      CookieHelper.setCookie('adminTemplate', 'rightSidebar', 30);
    },
    setTopSidebar: function() {
      console.log("Setting TopSidebar Template!");
      this.componentLeft = "AdminSidebar";
      this.componentRight = "AdminInner";
      this.templateLayout = "topSidebar";
      CookieHelper.setCookie('adminTemplate', 'topSidebar', 30);
    }
  },
  created() {
    var cookieValHelp = CookieHelper.getCookie('adminTemplate');
    console.log('CookieValue[adminTemplate]: '+cookieValHelp);
    if (cookieValHelp != ""){
      this.templateLayout = cookieValHelp;
      if (["default", "rightSidebar","topSidebar"].includes(this.templateLayout)) {
        this.setAdminTemplate(this.templateLayout);
      } else {
        this.setDefaultOrder();
        console.log('AdminContainer.data.templateLayout already set!')
      };
    } else {
      this.setDefaultOrder();
    }
  }
};
</script>

<style lang="scss" scoped>
.adminContainer {
  color: white;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  
  .adminPageContent {
    display: flex;
    flex-direction: row;
    flex: 1;
  }
}
.adminContainer.topSidebar {
  
  .adminPageContent {
    display: flex;
    flex-direction: column;
    flex: 1;

    .adminSidebar {
      flex-direction: row;
    }
  }
}
</style>
