<template>
  <div class="AdminPageRoute">
    <admin-navigation />
  </div>
</template>
<script>
import AdminNavigation from "@/Admin/AdminNavigation.vue";
export default {
  name: "AdminPageRoute",
  components: { AdminNavigation },
  data() {
    return {};
  },
};
</script>
<style lang="scss" scoped>
.AdminPageRoute {
  width: 100%;
  min-height: 100vh;
}
.app-route {
  width: 100%;
  min-height: calc(100vh - 64px);
}
</style>
