<template>
  <div class="TheShowRoomPage grey lighten-3">
    <ShowRoomBtnsNavgition />
    <div class="router">
      <router-view> </router-view>
    </div>
    <!-- bottom navigation for seller -->
    <div class="hidden-md-and-up">
      <v-bottom-navigation
        :class="active ? 'nav-top' : ''"
        height="50"
        class="first-nav elevation-0"
        background-color="white"
        active-class="blue--text"
        light
        flat
        fixed
        grow
      >
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
        >
          <span class="text">الرئيسية</span>
          <v-icon>mdi-home-variant </v-icon>
        </v-btn>

        <v-btn @click.stop="dialog = true">
          <span class="text">القائمة</span>
          <v-icon>mdi-dots-grid </v-icon>
        </v-btn>

        <v-btn to="/MyOrder">
          <span class="text">الطلبات</span>
          <v-icon>mdi-truck-delivery </v-icon>
        </v-btn>
        <v-btn v-if="!active" @click="active = !active">
          <span class="text">المزيد</span>
          <v-icon>mdi-chevron-down </v-icon>
        </v-btn>
        <v-btn v-else @click="active = !active">
          <span class="text">رجوع</span>
          <v-icon>mdi-chevron-up </v-icon>
        </v-btn>
      </v-bottom-navigation>
      <v-bottom-navigation
        height="50"
        background-color="white"
        active-class="blue--text"
        class="elevation-0"
        light
        flat
        fixed
        grow
      >
        <!-- <v-btn to="/">
        <span class="text">الرئيسية</span>
        <v-icon>mdi-home-variant </v-icon>
      </v-btn> -->

        <v-btn
          :to="{
            name: 'SmallScreenNotification',
            params: { Notfication: 'الأشعارات' },
          }"
        >
          <span class="text">الدردشة</span>
          <v-icon>mdi-forum-outline </v-icon>
        </v-btn>
        <v-btn to="/TheShowRoomPage">
          <span class="text">تعليق الزبون</span>
          <v-icon>mdi-comment-multiple </v-icon>
        </v-btn>
        <v-btn to="/TheUserPageView">
          <span class="text"> إعلان</span>
          <v-icon>mdi-square-rounded </v-icon>
        </v-btn>
        <v-btn to="/TheUserPageView">
          <span class="text"> مساعدة</span>
          <v-icon>mdi-tooltip-question </v-icon>
        </v-btn>
      </v-bottom-navigation>
    </div>
    <!-- menue small screen -->
    <v-dialog no-click-animation persistent v-model="dialog" max-width="300">
      <v-card class="pa-3" color="grey lighten-3">
        <v-card-actions
          class="flex-wrap justify-space-around card-actions pa-0"
        >
          <v-card
            flat
            @click="dialog = false"
            rounded="lg"
            class="my-1 menu-card"
            v-for="item in MenuLinks"
            :key="item"
            link
            width="45%"
            exact-path
            :to="item.RouterName"
          >
            <v-row no-gutters class="pa-0 pt-1 justify-center">
              <v-icon
                :class="item.class"
                class="icon"
                v-text="item.icon"
              ></v-icon>
            </v-row>
            <span class="link mt-2" v-text="item.link"></span>
          </v-card>
        </v-card-actions>
        <v-card-actions class="pa-2">
          <v-btn
            elevation="0"
            class="close-dialog"
            block
            @click="dialog = false"
          >
            إغلاق
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
// import Cars from "./ShowRoomCars.vue";
// import Info from "./ShowRoomCarsInfo.vue";
import ShowRoomBtnsNavgition from "./StoreNavigation.vue";
export default {
  name: "TheShowRoomPage",
  components: { ShowRoomBtnsNavgition },
  data() {
    return {
      active: false,
      dialog: false,
      search: "",
      MenuLinks: [
        {
          link: "المنتجات",
          icon: "mdi-package-variant",
          class: "MyProduct",
          RouterName: "/StoreProducts",
        },
        {
          link: "المبيعات",
          icon: "mdi-point-of-sale",
          class: "MySales",
          RouterName: "/MyOrder",
        },
        {
          link: "الدخل",
          icon: "mdi-cash",
          class: "MyIncome",
          RouterName: "/StoreIncome",
        },
        {
          link: "رؤى الأعمال",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        {
          link: "تسويق",
          icon: "mdi-percent-circle",
          class: "MyMarketingCentre",
          RouterName: "/Marketing",
        },
        {
          link: "إعدادات المتجر",
          icon: "mdi-cog-outline",
          class: "ShopSettings",
          RouterName: "/StoreProfile",
        },
      ],
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
.menu-card {
  height: 80px;
  width: 90px;
  // @media (max-width: 600px) {
  //   height: 100px;
  //   width: 85px;
  // }
}
.link {
  font-size: 14px !important;
  font-weight: 600;
  letter-spacing: 0;
  color: $fontcolor !important;
  font-family: $fontfamliy3;
  display: flex;
  justify-content: center;
}
.icon {
  font-size: 30px !important;
  border-radius: 50%;
  padding: 5px;
  color: #fff !important;
}
.close-dialog {
  font-family: sans-serif !important;
  font-size: 15px !important;
  letter-spacing: 0 !important;
  font-weight: 600;
}
.MyProduct {
  background: linear-gradient(30deg, #536dfe 50%, #8c9eff 100%);
}
.MySales {
  background: linear-gradient(30deg, #f57c00 50%, #fb8c00 100%);
}
.MyBusinessInsights {
  background: linear-gradient(30deg, #00b0ff 50%, #40c4ff 100%);
}
.MyMarketingCentre {
  background: linear-gradient(30deg, #dd2c00 50%, #ff3d00 100%);
}
.MyIncome {
  background: linear-gradient(30deg, #43a047 50%, #66bb6a 100%);
}
.ShopSettings {
  background: linear-gradient(30deg, #757575 50%, #bdbdbd 100%);
}
</style>
