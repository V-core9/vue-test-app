<template>
  <div class="adminFooter">
    Footer Part
    <button @click="$emit('set-admin-template', 'default')">Set Default Template</button>
    <button @click="$emit('set-admin-template', 'rightSidebar')">Set rightSidebar Template</button>
    <button @click="$emit('set-admin-template', 'topSidebar')">Set topSidebar Template</button>
  </div>
</template>

<script>
export default {
  name: "AdminFooter",
  components: {}
};
</script>

<style lang="scss" scoped>
.adminFooter {
  background: #333;
}
</style>
