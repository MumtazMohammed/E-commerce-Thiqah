<template>
  <v-app id="inspire">
    <v-main class="grey lighten-3 pa-0">
      <v-container fluid>
        <v-row>
          <!-- side tabs   -->
          <v-col cols="2" class="pt-0 pr-0">
            <v-sheet
              class="overflow-auto example"
              color="white"
              height="100vh"
              rounded="0"
            >
              <v-card class="pa-2 ma-2" router to="/">
                <v-row no-gutters justify="center" align="center">
                  <h3 class="logo-text">ثــــقـــة لتجارة الأكترونية</h3>
                  <v-icon
                    class="ma-1"
                    style="
                      background-color: #fc624d;
                      padding: 3px;
                      border-radius: 50%;
                      color: white;
                    "
                    size="20"
                  >
                    mdi-shopping
                  </v-icon>
                </v-row>
              </v-card>
              <v-tabs
                slider-size="3"
                class="tab"
                color="grey darken-1"
                vertical
              >
                <v-tab
                  :to="{
                    name: 'MainStorePage',
                  }"
                  class="tab"
                >
                  الصفحة الرئيسية
                  <v-spacer></v-spacer>
                  <v-icon> mdi-home </v-icon>
                </v-tab>
                <!-- <v-tab
                    :to="link.RouterName"
                    v-for="link in Toplinks"
                    :key="link"
                  >
                    {{ link.link }}
                  </v-tab> -->
                <v-tab
                  link
                  :to="link.RouterName"
                  v-for="(link, i) in links"
                  :key="i"
                >
                  {{ link.link }}
                  <v-spacer></v-spacer>
                  <v-icon> {{ link.icon }} </v-icon>
                </v-tab>
              </v-tabs>
            </v-sheet>
          </v-col>
          <!-- router   -->
          <v-col cols="8" class="pt-0">
            <v-sheet
              class="overflow-y-auto example"
              color="transparent"
              height="100vh"
              rounded="0"
            >
              <router-view> </router-view>
            </v-sheet>
          </v-col>
          <!-- new order  -->
          <v-col cols="2" class="pt-0 pl-0">
            <v-sheet rounded="0" class="overflow-y-auto example" height="100vh">
              <v-banner sticky>
                <v-card-title class="Marketing-text justify-center white py-2">
                  <v-avatar
                    class="ml-2 white--text"
                    size="20"
                    color="green accent-4"
                  >
                    8
                  </v-avatar>
                  طلبات جديدة
                </v-card-title>
              </v-banner>
              <v-row no-gutters>
                <v-col
                  v-for="(Car, i) in ShowRoomUserCars"
                  :key="i"
                  cols="12"
                  class="my-1"
                >
                  <v-card
                    :to="{
                      name: 'ProductsOnClickShowDetail',
                      params: {
                        carId: Car.id,
                      },
                    }"
                    height="100%"
                    class="overflow-hidden"
                    flat
                  >
                    <v-row justify="center" align="center" no-gutters>
                      <!-- Products main Img  -->
                      <v-col cols="4" class="text-center">
                        <v-avatar tile size="50">
                          <v-img
                            :src="getimageUrl(Car.folder, Car.image)"
                            :lazy-src="getimageUrl(Car.folder, Car.image)"
                            alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                          ></v-img>
                        </v-avatar>
                      </v-col>
                      <!-- Car detail -->
                      <v-col cols="8">
                        <v-card-text class="detail pa-1 text-truncate">
                          <span> {{ Car.company }} {{ Car.name }} </span>
                          ,
                          <span> طويل </span>
                          ,
                          <span> أسود </span>
                          ,
                          <span> 1 </span>
                        </v-card-text>
                      </v-col>
                      <!-- <v-spacer></v-spacer>
                        <span class="price-cat pt-0 pa-1">
                          {{ Car.payment }}
                          <span>ريال</span>
                        </span> -->
                    </v-row>
                    <v-divider></v-divider>
                  </v-card>
                </v-col>
              </v-row>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
export default {
  data() {
    return {
      ShowRoomUserCars,
      carId: this.$route.params.carId,
      Toplinks: [
        // {
        //   link: "المنتجات",
        //   icon: "mdi-package-variant",
        //   class: "MyProduct",
        //   RouterName: "/StoreProducts",
        // },
        // {
        //   link: "المبيعات",
        //   icon: "mdi-point-of-sale",
        //   class: "MySales",
        //   RouterName: "/MyOrder",
        // },
        // {
        //   link: "إضافة منتج",
        //   icon: "mdi-point-of-sale",
        //   class: "MySales",
        //   RouterName: "/AddNewProducts",
        // },
        // {
        //   link: "الدخل",
        //   icon: "mdi-cash",
        //   class: "MyIncome",
        //   RouterName: "/StoreIncome",
        // },
        {
          link: "رؤى الأعمال",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        {
          link: "متجري ",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        // {
        //   link: "تسويق",
        //   icon: "mdi-percent-circle",
        //   class: "MyMarketingCentre",
        //   RouterName: "/Marketing",
        // },
        // {
        //   link: "إعدادات المتجر",
        //   icon: "mdi-cog-outline",
        //   class: "ShopSettings",
        //   RouterName: "/StoreProfile",
        // },
      ],
      links: [
        {
          link: "المنتجات",
          icon: "mdi-package-variant",
          class: "MyProduct",
          RouterName: "/StoreProducts",
        },
        {
          link: "المبيعات",
          icon: "mdi-storefront",
          class: "MySales",
          RouterName: "/MyOrder",
        },
        {
          link: "إضافة منتج",
          icon: "mdi-plus",
          class: "MySales",
          RouterName: "/AddNewProducts",
        },
        {
          link: "الدخل",
          icon: "mdi-cash",
          class: "MyIncome",
          RouterName: "/StoreIncome",
        },
        // {
        //   link: "رؤى الأعمال",
        //   icon: "mdi-finance",
        //   class: "MyBusinessInsights",
        //   RouterName: "/BusinessInsights",
        // },
        {
          link: "تسويق",
          icon: "mdi-percent-circle",
          class: "MyMarketingCentre",
          RouterName: "/Marketing",
        },
        {
          link: "رؤى الأعمال",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        {
          link: "متجري ",
          icon: "mdi-finance",
          class: "MyBusinessInsights",
          RouterName: "/BusinessInsights",
        },
        // {
        //   link: "إعدادات المتجر",
        //   icon: "mdi-cog-outline",
        //   class: "ShopSettings",
        //   RouterName: "/StoreProfile",
        // },
      ],
      items: [
        {
          id: 1,
          name: "المبيعات :",
          children: [
            { id: 2, name: "الطلبات " },
            { id: 3, name: " بإنتظار شحن المنتج " },
            { id: 4, name: " طلبات ألغيت " },
          ],
        },
        {
          id: 5,
          name: "المنتجات",
          children: [
            {
              id: 6,
              name: "الكل",
            },
            {
              id: 7,
              name: "مباع",
            },
            {
              id: 8,
              name: "موقف",
            },
          ],
        },
        {
          id: 15,
          name: "Downloads :",
          children: [
            { id: 16, name: "October : pdf" },
            { id: 17, name: "November : pdf" },
            { id: 18, name: "Tutorial : html" },
          ],
        },
        {
          id: 19,
          name: "Videos :",
          children: [
            {
              id: 20,
              name: "Tutorials :",
              children: [
                { id: 21, name: "Basic layouts : mp4" },
                { id: 22, name: "Advanced techniques : mp4" },
                { id: 23, name: "All about app : dir" },
              ],
            },
            { id: 24, name: "Intro : mov" },
            { id: 25, name: "Conference introduction : avi" },
          ],
        },
      ],
      ToDoList: [
        {
          ToDoName: "الطلبات",
          ToDoNumber: 0,
        },
        {
          ToDoName: "الربح ",
          ToDoNumber: 0,
        },
        {
          ToDoName: "الزائرين",
          ToDoNumber: 0,
        },
        {
          ToDoName: "الطلبات الملغية",
          ToDoNumber: 0,
        },
      ],
    };
  },
  computed: {
    filteredStore: function () {
      return this.ShowRoomUserCars.filter((ShowRoomUserCars) => {
        return ShowRoomUserCars.name.match(this.search);
      });
    },
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
    reset() {
      return (this.search = "");
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Marketing-text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  color: $fontcolor;
  font-size: 17px;
}
.logo-text {
  font-family: $fontfamliy3;
  color: $color-2 !important;
  font-weight: 600 !important;
  font-size: 16px !important;
}
a {
  text-decoration: none;
}
.detail {
  font-family: $fontfamliy3;
  font-size: 13px !important;
}
.text-to-all {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
::v-deep a.v-tab {
  font-size: 17px !important;
  font-weight: 600px;
  letter-spacing: 0 !important;
  font-family: $fontfamliy3;
}
.price-cat {
  font-family: sans-serif;
  font-size: 15px !important;
  font-weight: 700;
  color: $color-2;
}
.user-name {
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
}
.offers-card::-webkit-scrollbar {
  width: 0.5em;
}
.offers-card::-webkit-scrollbar-track {
  background-color: #eee;
}
.offers-card::-webkit-scrollbar-thumb {
  background-color: darkgrey;
}
::v-deep .v-treeview-node__level {
  width: 0px;
}
::v-deep .v-treeview-node.v-treeview-node--leaf.v-treeview-node--click {
  color: $color-2;
}
::v-deep .v-banner__wrapper {
  padding: 0 !important;
  border: 0 !important;
}
// .example::-webkit-scrollbar {
//   display: none;
// }
.example::-webkit-scrollbar {
  width: 0.5em;
}

.example::-webkit-scrollbar-track {
  //   box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  background-color: #f5f5f5;
}

.example::-webkit-scrollbar-thumb {
  background-color: #e0e0e0;
  border-radius: 3px;
}
</style>
