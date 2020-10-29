<template>
  <div class="adminSidebar" v-bind:class="{'toggledSidebar':sidebarStatus}">
    <div class="adminSidebarInner">
        <AdminNavigation />
        <AdminNavigation />
        <AdminNavigation />
        <AdminNavigation />
    </div>
    <div class="botOptions">
        <button @click="setSidebarMode">
            <font-awesome-icon :icon="homeIcon" />
            <p>Toggle Sidebar</p>
        </button>
    </div>
  </div>
</template>

<script>
import CookieHelper from "@/components/helpers/CookieHelper.js";
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faSpinner, faAngleDoubleRight, faAngleDoubleLeft } from '@fortawesome/free-solid-svg-icons'
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
        leftArr: faAngleDoubleLeft,
        rightArr: faAngleDoubleRight,
    }
  },
  methods: {
      setSidebarMode : function() {
            if (CookieHelper.getCookie('sidebarStatus') != "true"){
                this.sidebarStatus = true;
                this.homeIcon = this.rightArr;
                CookieHelper.setCookie('sidebarStatus', true, 30);
            } else {
                this.sidebarStatus = false;
                this.homeIcon = this.leftArr;
                CookieHelper.setCookie('sidebarStatus', false, 30);
            }
      },
      getSidebarMode : function() {
            if (CookieHelper.getCookie('sidebarStatus') == "true"){
                this.sidebarStatus = true;
                this.homeIcon = this.rightArr;
            } else {
                this.homeIcon = this.leftArr;
            }
      }
  },
  created() {
      this.getSidebarMode();
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

    .botOptions {

        p {
            font-size: 0;
        }
    }
}

.topSidebar {        
    .adminSidebar {
        width: inherit;

        .adminSidebarInner {
            display: flex;
            flex-direction: row;

            #navAdmin{
                flex-direction: row;
            }
        }
        
        .botOptions {
            display: flex;

            button {
                display: flex;
                align-items: center;
                gap: 1em;
            }
        }
    }
}
</style>
