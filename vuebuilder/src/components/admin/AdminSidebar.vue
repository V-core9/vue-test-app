<template>
  <div class="adminSidebar" v-bind:class="{'toggledSidebar':this.sidebarStatus}">
    <div class="adminSidebarInner">
        <AdminNavigation />
        <AdminNavigation />
        <AdminNavigation />
        <AdminNavigation />
    </div>
    <div class="botOptions">
        <button @click="toggleSidebar">
            <font-awesome-icon :icon="adminIcon" />
            Toggle Sidebar
        </button>
    </div>
  </div>
</template>

<script>
import CookieHelper from "@/components/helpers/CookieHelper.js";
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faSpinner, faUsers, faAngleDoubleLeft } from '@fortawesome/free-solid-svg-icons'
import AdminNavigation from "@/components/layouts/AdminNavigation.vue";

export default {
  name: "AdminSidebar",
  components: {
    AdminNavigation,
    FontAwesomeIcon
    },
  data () {
    return {
        sidebarStatus: false,
        homeIcon: faSpinner,
        aboutIcon: faUsers,
        adminIcon: faAngleDoubleLeft,
    }
  },
  methods: {
      toggleSidebar : function() {
            alert('toggle sidebar');
            if (CookieHelper.getCookie('sidebarStatus') != ""){
                this.sidebarStatus = true;
                CookieHelper.setCookie('sidebarStatus', true, 30);
            } else {
                this.sidebarStatus = false;
                CookieHelper.setCookie('sidebarStatus', false, 30);
            }
      }
  },
  created() {
      this.toggleSidebar();
  }
};
</script>

<style lang="scss" scoped>
.adminSidebar {
    background: white;
    display: flex;
    flex-direction: column;
    min-width: 310px;
    text-align: left;
    border-top: 1px solid black;
    
    .adminSidebarInner {
        flex: 1;

        #navAdmin {
            display: flex;
            flex-direction: column;
        }
    }

    .botOptions {
        display: flex;
        flex-direction: row;
        
        button {
            flex: 1;
            padding: 5px 10px;
        }
    }
}
.adminSidebar.toggledSidebar {
    min-width: unset;
    width: min-content;
}

.topSidebar {

    #navAdmin{
        flex-direction: row;
    }
}
</style>
