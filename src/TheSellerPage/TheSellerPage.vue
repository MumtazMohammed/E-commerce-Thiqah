<template>
  <div class="TheShowRoomPage grey lighten-3">
    <div class="">
      <TheSellerPageBigScreen class="hidden-sm-and-down" />
      <div class="router hidden-md-and-up">
        <router-view> </router-view>
      </div>
    </div>
  </div>
</template>
<script>
// import Cars from "./ShowRoomCars.vue";
// import Info from "./ShowRoomCarsInfo.vue";
import TheSellerPageBigScreen from "./TheSellerPageBigScreen.vue";

export default {
  name: "TheShowRoomPage",
  components: {  TheSellerPageBigScreen },
  data() {
    return {
      active: false,
      search: "",
    };
  },
  computed: {
    filteredStore: function () {
      return this.showrooms.filter((showroom) => {
        return showroom.ShowroomName.match(this.search);
      });
    },
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1);
    },
    length() {
      return 7000;
    },
  },
  methods: {
    reset() {
      return (this.search = "");
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheShowRoomPage {
  width: 100%;
  min-height: 100vh;
  // background-color: $backgroundcard;

  .router {
    @media (max-width: 600px) {
      // padding: 15px;
    }
  }
}
.text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  margin-top: 5px;
  font-size: 14px;
}
::v-deep
  .v-bottom-navigation.first-nav.v-item-group.theme--light.v-bottom-navigation--fixed.white {
  z-index: 12 !important;
}
::v-deep .v-item-group.v-bottom-navigation--fixed {
  z-index: 11 !important;
}
.first-nav {
  z-index: 13 !important;
}
.nav-top {
  bottom: 50px !important;
}
// menue
</style>
