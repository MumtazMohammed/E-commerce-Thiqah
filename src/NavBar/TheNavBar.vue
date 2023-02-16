<template>
  <nav class="elevation-0 nav">
    <v-system-bar window class="px-4 hidden-xs-only grey lighten-3" height="40">
      <LogingAndSignup />
    </v-system-bar>
    <SearchBar />
  </nav>
</template>

<script>
// import Navlinks from "./NavLinks.vue";
import LogingAndSignup from "./LogingAndSignup.vue";
import SearchBar from "../Search/SearchBar.vue";
// import StartToSellYourCar from "./StartToSellYourCar.vue";

export default {
  name: "navbar",
  components: {
    LogingAndSignup,
    SearchBar, // StartToSellYourCar,
  },
  data: () => ({
    drawer: false,
    welcomeTouser: "مرحباً ,",
    model: 1,
  }),
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";

::v-deep
  .v-system-bar.px-4.hidden-sm-and-up.grey.lighten-3.v-system-bar--window.theme--light {
  // background-color: $color-2 !important;
  @media (max-width: 600px) {
    display: none;
  }
}
</style>
