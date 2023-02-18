<template>
  <div>
    <div class="ShowRoomBtnsNavgition">
      <v-app-bar flat clipped-right color="#fff">
        <!-- <v-btn
          class="hidden-md-and-up"
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon size="27" color="#fc624d">mdi-home</v-icon>
        </v-btn> -->
        <!-- chat  -->
        <!-- small screen chat  -->
        <v-btn
          class="hidden-md-and-up btn-noti-cart"
          :to="{
            name: 'SmallScreenNotification',
            params: { Notfication: 'الأشعارات' },
          }"
          icon
          @click.stop="showMsg = !showMsg"
        >
          <v-badge color="red" dot overlap left bordered>
            <v-icon size="25" color="">mdi-bell-outline</v-icon>
          </v-badge>
        </v-btn>
        <!-- smalll menu  -->
        <v-divider vertical class="ml-2 hidden-md-and-up"></v-divider>
        <!-- store name and click to setting -->
        <v-card
          flat
          rounded="lg"
          class=""
          color="grey lighten-2"
          max-width="200px"
          to="/StoreProfile"
        >
          <v-card-actions class="pa-1">
            <v-avatar size="30" color="grey"> </v-avatar>
            <span class="mr-1 text-truncate user-name"
              >وقت العطور رررسسسسسسسر</span
            >
          </v-card-actions>
        </v-card>
        <v-spacer></v-spacer>

        <!-- go to main page  -->
        <v-btn icon to="/" class="tab" exact-path>
          <v-icon>mdi-arrow-left </v-icon>
        </v-btn>
      </v-app-bar>
      <!-- navigation menu   -->
      <v-sheet class="py-2 px-1 hidden-sm-and-down">
        <v-chip-group mandatory active-class="blue--text text--accent-4">
          <v-chip
            class="link"
            :to="{
              name: 'MainStorePage',
              params: { MyCar: 'إعلاناتي' },
            }"
          >
            الصفحة الرئيسية
          </v-chip>
          <v-chip
            class="link"
            v-text="item.link"
            :to="item.RouterName"
            v-for="item in MenuLinks"
            :key="item"
          >
          </v-chip>
        </v-chip-group>
      </v-sheet>
    </div>
  </div>
</template>
<script>
export default {
  name: "ShowRoomBtnsNavgition",
  data() {
    return {
      drawer: false,
      group: null,
      dialog: false,
      showMsg: false,
      show: false,
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
          link: "إضافة منتج",
          icon: "mdi-point-of-sale",
          class: "MySales",
          RouterName: "/AddNewProducts",
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
        // {
        //   link: "إعدادات المتجر",
        //   icon: "mdi-cog-outline",
        //   class: "ShopSettings",
        //   RouterName: "/StoreProfile",
        // },
      ],
    };
  },
  watch: {
    group() {
      this.drawer = false;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ShowRoomBtnsNavgition {
  width: 100%;
  height: auto;
  position: relative;
}
.menu-card {
  height: 80px;
  width: 90px;
  // @media (max-width: 600px) {
  //   height: 100px;
  //   width: 85px;
  // }
}
.tab {
  color: $color-2 !important;
  font-size: 18px !important;
  font-weight: 600px;
  letter-spacing: 0 !important;
}
.main-page::v-deep .v-slide-group__content.v-tabs-bar__content {
  justify-content: flex-end;
}

.user-name {
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
}

.card-actions {
  width: 100%;
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
.btn-noti-cart {
  color: $color-2 !important;
  // background-color: #eee;

  @media (max-width: 600px) {
    border: none !important;
    font-size: 17px !important;
  }
}
::v-deep .v-slide-group__content {
  justify-content: center;
}
</style>
