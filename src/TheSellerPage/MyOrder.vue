<template>
  <div class="UserAdd">
    <!-- small Screen Tabs  -->
    <div class="hidden-md-and-up">
      <v-app-bar flat fixed color="#fc624d" dark>
        <!-- <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-home </v-icon>
        </v-btn>
        <v-toolbar-title class="pr-1 titel">الرئيسية</v-toolbar-title> -->
        <v-card-title class="normal-text-edite pa-2">
          <span class="ml-2">{{ ShowRoomUserCars.length }}</span>
          طلب جديد
        </v-card-title>
        <v-spacer></v-spacer>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-arrow-left </v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet height="56"></v-sheet>
    </div>
    <!-- order Tabs  -->
    <v-sheet>
      <v-tabs
        slider-size="2"
        color="grey darken-1"
        v-model="tab"
        rounded="dm"
        grow
        :show-arrows="false"
      >
        <v-tab href="#tab-1" class="links"> بإنتظار الشحن </v-tab>
        <v-tab href="#tab-2" class="links"> تم الشحن </v-tab>
        <v-tab href="#tab-4" class="links"> مكتمل </v-tab>
        <v-tab href="#tab-4" class="links"> ملغي </v-tab>
        <v-tab href="#tab-4" class="links"> مرتجع </v-tab>
      </v-tabs>
      <v-card flat tile style="" color="grey lighten-2 card-height">
        <v-tabs-items v-model="tab" class="pa-0 transparent">
          <!-- shipping order  -->
          <v-tab-item value="tab-1">
            <v-card-title class="normal-text-edite hidden-sm-and-down pa-2">
              <span class="ml-2">{{ ShowRoomUserCars.length }}</span>
              الطلبات
            </v-card-title>
            <v-card
              flat
              tile
              class="mx-auto example mb-2"
              style="height: calc(100vh - 105px); overflow-y: scroll"
            >
              <!-- <v-divider></v-divider> -->
              <!-- order card  -->
              <v-row no-gutters>
                <v-col
                  v-for="(Car, i) in ShowRoomUserCars"
                  :key="i"
                  cols="12"
                  class="pa-1"
                >
                  <v-card outlined>
                    <v-row align="center" no-gutters>
                      <!-- buyer Info  -->
                      <v-col
                        class="mb-1"
                        style="border-bottom: 1px solid #eee"
                        cols="12"
                      >
                        <v-row align="center" no-gutters class="pa-2">
                          <!-- profile image  -->
                          <v-avatar size="25" color="grey"> </v-avatar>
                          <!-- name  -->
                          <span
                            style="font-size: 13px"
                            class="normal-text-edite mr-2"
                          >
                            محمد أمين
                          </span>
                          <v-spacer></v-spacer>
                          <!-- order number   -->
                          <span style="font-size: 13px">رقم الطلب : </span>
                          <span
                            class="mr-2"
                            style="
                              font-size: 13px;
                              font-family: sans-serif;
                              font-weight: 600;
                            "
                            >MMDO461514622151</span
                          >
                        </v-row>
                      </v-col>
                      <!-- order name & imag  -->
                      <v-col cols="5">
                        <v-row align="center" no-gutters>
                          <!-- imag  -->
                          <v-col cols="4" lg="2" sm="2" md="2">
                            <v-avatar tile size="50">
                              <v-img
                                :src="getimageUrl(Car.folder, Car.image)"
                                :lazy-src="getimageUrl(Car.folder, Car.image)"
                                alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                              ></v-img>
                            </v-avatar>
                          </v-col>
                          <!-- name  -->
                          <v-col cols="8" lg="10" sm="10" md="10">
                            <v-card-text
                              class="pa-2 normal-text-edite text-truncate d-block"
                            >
                              {{ Car.company }} {{ Car.name }}
                            </v-card-text>
                          </v-col>
                        </v-row>
                      </v-col>
                      <!-- total order -->
                      <v-col cols="1">
                        <v-card-text class="pa-0 text-truncate d-block">
                          {{ Car.payment }}
                        </v-card-text>
                      </v-col>
                      <!-- client's request -->
                      <v-col cols="4">
                        <v-card-text
                          class="pa-2 normal-text-edite text-truncate d-block"
                        >
                          {{ Car.discription }}
                        </v-card-text>
                      </v-col>
                      <!-- client's shipping request -->
                      <v-col cols="2">
                        <v-card-text
                          class="pa-2 normal-text-edite text-truncate d-block"
                        >
                          {{ Car.negotiable }}
                        </v-card-text>
                      </v-col>
                    </v-row>
                  </v-card>
                </v-col>
              </v-row>
            </v-card>
          </v-tab-item>
          <!-- Confirm for shipping -->
          <v-tab-item style="min-height: 100vh; overflow-y: auto" value="tab-2">
            <v-col v-for="i in 2" :key="i" cols="12" class="pa-2">
              <v-card
                width="100%"
                min-height="300"
                max-height="390"
                v-scroll.self="onScroll"
                class="overflow-y-auto overflow-x-hidden pa-1"
                color=""
              >
                <span class="title pa-0 pr-2 grey--text text--darken-2"
                  >معلومات الشحن
                </span>
                <v-simple-table class="rounded-0" dense>
                  <template v-slot:default>
                    <tbody>
                      <tr v-for="item in CustomerInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info">{{ item.calories }}</td>
                      </tr>
                      <tr v-for="item in ShipmentInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info pb-1">
                          <v-text-field
                            dense
                            placeholder="أدخل المعلومات"
                            class="pt-0 ma-0"
                            hide-details=""
                          ></v-text-field>
                        </td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
                <v-card-actions class="justify-center">
                  <v-btn outlined class="btn2">تأكيد الطلب</v-btn>
                  <v-btn outlined class="btn2"> إلغاء الطلب</v-btn>
                  <v-btn outlined class="btn2"> مراسلة العميل</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-tab-item>
          <!-- Cancelled Products -->
          <v-tab-item style="min-height: 100vh; overflow-y: auto" value="tab-4">
            <v-col v-for="i in 2" :key="i" cols="12" class="py-2 pa-0">
              <v-card
                width="100%"
                min-height="250"
                max-height="300"
                v-scroll.self="onScroll"
                class="overflow-y-auto overflow-x-hidden"
                color=""
              >
                <v-card-actions class="pa-0">
                  <v-btn class="client-Info" small elevation="0" tile>
                    حذف
                  </v-btn>
                  <v-btn class="client-Info" small elevation="0" tile>
                    طباعة
                  </v-btn>
                  <v-spacer></v-spacer>
                  <span class="client-Info pl-3">15 / 10 / 2020</span>
                </v-card-actions>
                <span class="title pa-0 pr-2 grey--text text--darken-2"> </span>
                <v-simple-table class="rounded-0" dense>
                  <template v-slot:default>
                    <tbody>
                      <tr>
                        <td class="client-Info">رقم المنتج</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                        <td class="client-Info text-center">11115104485</td>
                      </tr>
                      <tr>
                        <td class="client-Info">عدد</td>
                        <td class="client-Info text-center">1</td>
                        <td class="client-Info text-center">2</td>
                        <td class="client-Info text-center">1</td>
                        <td class="client-Info text-center">1</td>
                      </tr>
                      <tr>
                        <td class="client-Info">السعر</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                        <td class="client-Info text-center">4214 ريال</td>
                      </tr>
                      <tr v-for="item in CustomerInfo" :key="item.name">
                        <td class="client-Info">{{ item.name }}</td>
                        <td class="client-Info text-center">
                          {{ item.calories }}
                        </td>
                        <td class="client-Info text-center">----</td>
                        <td class="client-Info text-center">----</td>
                        <td class="client-Info text-center">----</td>
                      </tr>
                    </tbody>
                  </template>
                </v-simple-table>
                <v-card dark tile flat color="green darken-1">
                  <v-card-actions class="">
                    <v-card-text class="pa-0">إجمالي السعر</v-card-text>
                    <v-card-text class="pa-0 text-center">
                      47851 ريال
                    </v-card-text>
                  </v-card-actions>
                </v-card>
              </v-card>
            </v-col>
          </v-tab-item>
        </v-tabs-items>
      </v-card>
    </v-sheet>
  </div>
</template>
<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
export default {
  name: "UserAdd",
  components: {},
  data() {
    return {
      ShowRoomUserCars,
      tab: null,
      CustomerInfo: [
        {
          name: " تاريخ الطلب ",
          DateTime: ["21 / 1 / 2022", "10:55 am"],
        },
        {
          name: "طلب رقم ",
          calories: "0147",
        },
        {
          name: "طلب رقم ",
          calories: "0147",
        },
      ],
      ProductInfo: [
        {
          name: "أسم المنتج",
          calories: "مـازدا مازدا3 مـازدا مازدا3 مـازدا مازدا3",
        },
        {
          name: "رقم المنتج ",
          calories: 1654218459,
        },
        {
          name: "الموديل",
          calories: 262,
        },
        {
          name: "المقاس",
          calories: 262,
        },
        {
          name: "اللون",
          calories: 262,
        },
        {
          name: "عدد",
          calories: 2,
        },
        {
          name: "إجمالي",
          calories: "1521 ريال",
        },
      ],
      ShipmentInfo: [
        {
          name: "أسم شركة التوصيل أو أسم موصل الطلب",
          calories: 159,
        },
        {
          name: "رقم هاتف التوصيل",
          calories: 237,
        },
        {
          name: "زمن توصيل المنتج",
          calories: 262,
        },
        {
          name: "رقم التوصيل ",
          calories: 159,
        },
      ],
      ShipmentArrived: [
        {
          calories: "النسر السريع",
          name: "أسم شركة التوصيل أو أسم موصل الطلب",
        },
        {
          calories: "0112151456",
          name: "رقم هاتف التوصيل",
        },
        {
          calories: 4,
          name: "زمن توصيل المنتج",
        },
        {
          name: "رقم التوصيل ",
          calories: "DE2550551",
        },
        {
          name: "عنوان التسليم",
          calories:
            "عنوانعنوانعنوانعنوانعنوانعنوانعنوانعنوان 1424 عنوانعنوانعنوانعنوانعنوان",
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
@import "../scss/virables";
@import "../scss/mixin";
.UserAdd {
  width: 100%;
  min-height: calc(100vh - 114px);
  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: #039be5 !important;
    font-size: 16px !important;
  }

  .btn2 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 14px !important;
  }
  .client-Info {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 16px !important;
  }
}

::v-deep .theme--light.v-tabs .v-tab:hover:before {
  opacity: 0 !important;
}
::v-deep span.v-stepper__step__step {
  margin-left: 0;
  margin-bottom: 10px;
}
::v-deep input::placeholder {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 13px;
}
.links {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 15px !important;
  @media (max-width: 600px) {
    font-size: 14px !important;
    font-weight: 600;
  }
}

.PerPrder {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 13px !important;
}
.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
.normal-text-edite {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  span {
    font-family: sans-serif !important;
    letter-spacing: 0.5px !important;
  }
}
// ::v-deep .v-banner__wrapper {
//   border: 0 !important;
//   padding: 0 !important;
// }
::v-deep
  .v-tabs:not(.v-tabs--vertical):not(.v-tabs--right)
  > .v-slide-group--is-overflowing.v-tabs-bar--is-mobile:not(.v-slide-group--has-affixes)
  .v-slide-group__prev {
  display: none !important;
}
.example::-webkit-scrollbar {
  display: none;
}
.card-height {
  height: calc(100vh - 48px);
  @media (max-width: 960px) {
    height: calc(100vh - 104px) !important;
  }
}
</style>
