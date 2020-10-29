<template>
  <div id="navAdmin">
    <router-link to="/">
       <font-awesome-icon :icon="homeIcon" />
       <p>Home</p>
    </router-link>
    <router-link to="/about">
       <font-awesome-icon :icon="aboutIcon" />
       <p>About</p>
    </router-link>
    <router-link to="/admin">
       <font-awesome-icon :icon="adminIcon" />
       <p>Admin</p>
    </router-link>
  </div>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faSpinner, faUsers, faTachometerAlt } from '@fortawesome/free-solid-svg-icons'

export default {
  name: "AdminNavigation",

  data () {
    return {
      homeIcon: faSpinner,
      aboutIcon: faUsers,
      adminIcon: faTachometerAlt,
    }
  },

  components: {
    FontAwesomeIcon
  }
};
</script>

<style  lang="scss" scoped>
#navAdmin {
    display: flex;
    flex-direction: row;
    
    a {
        padding: 7.5px 15px;
        color: #f0f0f0;
        transition: 0.25s ease all;
        text-decoration: none;
        display: flex;
        gap: 1em;

        svg{
            width: 1em;
            height: 1em;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        &:hover {
            background: #444;
            color: white;
        }

        &.router-link-exact-active {
            color: #00e2ff;

            &:hover {
                background: #444;
                color: white;
            }
        }
    }
}

.adminSidebar {

    #navAdmin{

        a{
            color: black;

            &:hover {
                background: #444;
                color: white;
            }
            

            &.router-link-exact-active {
                background: #1976d2;
                color: white;

                &:hover {
                    background: #444;
                    color: white;
                }
            }
        }
    }
}

.adminSidebar.toggledSidebar {

    #navAdmin{

        a {
            gap: 0;

            svg {

            }

            p {
                font-size: 0;
                width: 0;
                height: 0;
            }
        }
    }
}

.adminSidebar.topSidebar {

    .adminSidebarInner {

        #navAdmin{
            display: flex;
        }
    }
}
</style>