<template>
  <v-app id="inspire">
    <TheUserPageBigScreen class="hidden-sm-and-down" />
    <TheUserPageSmallScreen class="hidden-md-and-up" />
    <FixedBottomNav class="hidden-md-and-up" />
  </v-app>
</template>
<script>
import TheUserPageSmallScreen from "./SmallScreen/TheClientSmallScreenPage.vue";
import TheUserPageBigScreen from "./BigScreen/TheClientBigScreenPage.vue";
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
export default {
  name: "TheUserPageView",
  components: { TheUserPageBigScreen, TheUserPageSmallScreen, FixedBottomNav },
  // components: { NavigationUser },
  data() {
    return {
      drawer: false,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
#inspire {
  width: 100%;
  min-height: 100vh;
  background-color: #eee;
}
</style>
