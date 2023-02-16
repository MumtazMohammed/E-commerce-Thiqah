<template>
  <div>
    <v-bottom-navigation
      v-model="value"
      class="mt-50"
      height="50"
      background-color="white"
      active-class="active"
      light
      grow
      fixed
      style="z-index: 5"
    >
      <v-btn to="/">
        <span class="text">الرئيسية</span>
        <v-icon size="22">mdi-home-variant </v-icon>
      </v-btn>

      <v-btn>
        <span class="text">الفئات</span>
        <v-icon size="22">mdi-text-search-variant </v-icon>
      </v-btn>

      <v-btn>
        <span class="text">الإشعارات</span>
        <v-icon size="22">mdi-email-outline </v-icon>
      </v-btn>
      <v-menu
        nudge-bottom="-5px"
        nudge-left="11px"
        width="300"
        top
        transition="scroll-y-reverse-transition"
        offset-y
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on">
            <span class="text">حسابي</span>
            <v-icon size="22">mdi-account-outline </v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item to="/Login">
            <v-list-item-title>تسجيل الدخول</v-list-item-title>
          </v-list-item>
          <v-list-item to="/TheUserPageView">
            <v-list-item-title>صفحة العميل </v-list-item-title>
          </v-list-item>
          <v-list-item to="/TheSellerPage">
            <v-list-item-title>صفحة البائع </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-bottom-navigation>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: 1,
      drawer: false,
      type: "number",
      number: 0,
    };
  },
  // computed: {
  //   color() {
  //     switch (this.value) {
  //       case 0:
  //         return "grey darken-3";
  //       case 1:
  //         return "teal";
  //       case 2:
  //         return "brown";
  //       case 3:
  //         return "indigo";
  //       default:
  //         return "blue-grey";
  //     }
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "../scss/virables";

.text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  margin-top: 5px;
}
.active {
  color: $color-2 !important;
}
::v-deep .v-item-group.v-bottom-navigation .v-btn {
  min-width: 25% !important;
}
</style>
