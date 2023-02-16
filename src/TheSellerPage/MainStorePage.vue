<template>
  <div class="TheShowRoomPage">
    <v-container class="container pa-2">
      <v-dialog v-model="dialog" fullscreen>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            v-bind="attrs"
            v-on="on"
            elevation="0"
            dark
            icon
            class="btn blue darken-2 hidden-sm-and-up"
          >
            <v-icon>mdi-bullhorn</v-icon>
          </v-btn>
        </template>
        <v-sheet height="100%" class="grey lighten-3">
          <v-card-title class="text pa-1 grey--text text--darken-2">
            <v-icon size="26" color="green lighten-2" right
              >mdi-bullhorn-outline</v-icon
            >
            إعلان
            <v-spacer></v-spacer>
            <v-btn icon color="red">
              <v-icon @click="dialog = false"> mdi-close-thick </v-icon>
            </v-btn>
          </v-card-title>
          <v-row no-gutters>
            <v-col cols="12" class="pa-2">
              <!-- announcement (date) and announcement (number) -->
              <v-row
                justify="space-between"
                align="center"
                no-gutters
                class="px-1"
              >
                <small class="pa-0 text--disabled">5645</small>
                <small class="pa-0 text--disabled">5645</small>
              </v-row>
              <!-- announcement (title) -->
              <v-card flat class="pa-2">
                <v-row align="center" no-gutters style="flex-wrap: nowrap">
                  <v-card-text
                    class="Adv-titel py-0 pr-0 text-truncate text--secondary"
                  >
                    هل أستطيع التعديل على التنسيقات؟ هل أستطيع التعديل على
                    التنسيقات؟ هل أستطيع التعديل على التنسيقات؟
                    <v-spacer></v-spacer>
                  </v-card-text>
                  <!-- announcement (read or unread) -->
                  <v-icon light right size="15" color="red"> mdi-email</v-icon>
                  <!-- announcement (delete btn) -->
                  <v-btn icon>
                    <v-icon size="19" color=""> mdi-trash-can </v-icon>
                  </v-btn>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-sheet>
      </v-dialog>

      <!--  -->
      <v-row no-gutters>
        <v-col cols="4" class="hidden-sm-and-down pa-md-1 pa-lg-1">
          <v-card color="transparent" tile class="pa-" height="100%" flat>
            <v-card-title class="text py-1 grey--text text--darken-2">
              <v-icon color="green lighten-2" right>mdi-bullhorn</v-icon>
              إعلان
            </v-card-title>
            <v-row no-gutters>
              <v-col cols="12">
                <v-card
                  min-height="100%"
                  class="overflow-hidden"
                  color="#fff"
                  rounded="sm"
                  flat
                >
                  <div>
                    <v-subheader
                      class="Adv-titel pl-0 grey--text text--darken-1"
                    >
                      هل أستطيع التعديل على التنسيقات؟
                      <v-spacer></v-spacer>
                      <v-btn icon>
                        <v-icon size="19" color="red lighten-2">
                          mdi-trash-can
                        </v-icon>
                      </v-btn>
                    </v-subheader>
                    <v-card-text
                      class="Adv-text py-0 grey--text text--darken-1"
                    >
                      بلا شك، يمكنك تغيير النصوص والصور، اختيار ألوانك الخاصة،
                      ترتيب مكونات الصفحة بطريقتك، تغيير تقسيم الأعمدة… وأكثر،
                      كل ذلك بالسحب والإدراج وملء الخانات. ويمكنك أيضاً استخدام
                      التنسيق الواحد في أكثر من صفحة والتعديل عليها حسب ذوقك.
                    </v-card-text>
                  </div>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
        <v-col cols="12" md="8" lg="8" class="pa-md-1 pa-lg-1">
          <v-card height="400" flat class="mb-2 pa-2 overflow-y-auto">
            <v-card-title class="Marketing-text justify-center white py-2">
              <v-avatar
                class="ml-2 white--text"
                size="25"
                color="green accent-4"
              >
                8
              </v-avatar>
              طلبات جديدة
            </v-card-title>
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
                  <v-row align="center" no-gutters>
                    <!-- Products main Img  -->
                    <v-avatar rounded class="ml-2" size="70">
                      <v-img
                        contain
                        :src="getimageUrl(Car.folder, Car.image)"
                        :lazy-src="getimageUrl(Car.folder, Car.image)"
                        alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                      ></v-img>
                    </v-avatar>
                    <!-- Car detail -->
                    <v-col cols="5" md="8" lg="8">
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
                    <v-spacer></v-spacer>
                    <span class="price-cat pa-1">
                      {{ Car.payment }}
                      <span>ريال</span>
                    </span>
                  </v-row>
                  <!--  -->
                  <v-divider></v-divider>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
          <!-- To Do list  -->
          <v-card flat class="overflow-hidden mb-2 pa-2">
            <v-row no-gutters>
              <v-col
                md="6"
                lg="6"
                sm="6"
                cols="12"
                v-for="(ToDo, i) in ToDoList"
                :key="i"
                class="pa-1"
              >
                <v-card class="ToDoList-card">
                  <v-card-title class="subtitle pa-2">
                    {{ ToDo.ToDoName }}
                    <v-spacer></v-spacer>
                    <span class="blue--text text--darken-1 subtitle">
                      {{ ToDo.ToDoNumber }}
                    </span>
                  </v-card-title>
                  <v-sheet class="mx-auto" max-width="100%">
                    <v-sparkline
                      :value="value"
                      :smooth="9"
                      :padding="8"
                      :line-width="6"
                      stroke-linecap="round"
                      :gradient="['#F4511E', '#FF7043']"
                      type="trend"
                      auto-line-width="true"
                      auto-draw
                      color="grey"
                    >
                    </v-sparkline>
                  </v-sheet>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
          <v-card flat class="mb-2">
            <v-card-title class="Marketing-text justify-center white py-2">
              مركز التسويق والعروض
            </v-card-title>
            <v-row no-gutters>
              <v-col class="pa-3" cols="12">
                <v-card max-width="100%" class="pa-2">
                  <v-card-title class="text deep-orange--text pa-2 py-0">
                    عروض الجمعة
                    <v-spacer></v-spacer>
                    <v-btn
                      small
                      text
                      class="enter-theOffer px-2"
                      elevation="0"
                      color="green accent-4"
                    >
                      دخول العرض
                      <!-- <v-icon class="white--text">mdi-plus</v-icon> -->
                    </v-btn>
                  </v-card-title>
                  <v-alert
                    border="left"
                    colored-border
                    color="success"
                    elevation="0"
                    class="ma-0 pa0"
                    rounded="0"
                  >
                    <small class="mb-1"> 22 / 05 / 2020 </small>
                    <div class="text-offer">
                      ابتداً من التاريخ الموضح سيتم نشر العروض في الساعة
                      <span class="success--text mr-2">12:00 صباحاً</span>
                    </div>
                  </v-alert>
                  <v-divider inset></v-divider>
                  <v-alert
                    border="left"
                    colored-border
                    color="error"
                    elevation="0"
                    class="ma-0"
                    rounded="0"
                  >
                    <small class="mb-1"> 22 / 05 / 2020 </small>
                    <div class="text-offer">
                      ابتداً من التاريخ الموضح سيتم إغلاق العروض في الساعة
                      <span class="error--text mr-1">12:00 مساً</span>
                    </div>
                  </v-alert>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
          <v-card class="" flat>
            <v-card-title class="Marketing-titel pa-3"> التسويق </v-card-title>
            <v-row no-gutters>
              <v-col class="pa-2" cols="12" sm="6" md="6" lg="6">
                <v-card height="200">
                  <v-card-actions class="flex-column pb-0">
                    <v-icon class="icon-Marketing">mdi-star</v-icon>
                    <v-card-text class="text-center title-featur pa-2">
                      المنتجات المتميزة
                    </v-card-text>
                  </v-card-actions>
                  <v-card-text class="text-center text-featur pt-0 pa-2">
                    المنتجات المتميزةالمنتجات المتميزةالمنتجات المتميزةالمنتجات
                    المتميزةالمنتجات المتميزةالمنتجات المتميزةالمنتجات
                    المتميزةالمنتجات المتميزة
                  </v-card-text>
                </v-card>
              </v-col>
              <v-col class="pa-2" cols="12" sm="6" md="6" lg="6">
                <v-card height="200">
                  <v-card-actions class="flex-column pb-0">
                    <v-icon class="icon-Marketing"> mdi-ticket-percent </v-icon>
                    <v-card-text class="text-center title-featur pa-2">
                      قسائم
                    </v-card-text>
                  </v-card-actions>
                  <v-card-text class="text-center text-featur pt-0 pa-2">
                    قم بزيادة الطلبات من خلال تقديم أسعار مخفضة للمشترين عند
                    الخروج باستخدام القسائم.
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
// import VueApexCharts from "vue-apexcharts";
export default {
  name: "MainStorePage",
  components: {},
  data() {
    return {
      ToDolist: false,
      BusinessInsights: false,
      search: "",
      dialog: false,
      ShowRoomUserCars,
      carId: this.$route.params.carId,

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
      value: [0, 2, 5, 9, 5, 10, 3],
      labels: [
        "السبت",
        "الأحد",
        "الأثنين",
        "الثلاثاء",
        "الأربعاء",
        "الخميس",
        "الجمعة",
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
.TheShowRoomPage {
  width: 100%;
  min-height: 100vh;
  @media (max-width: 960px) {
    margin-bottom: 50px;
  }

  .text-offer {
    letter-spacing: 0 !important;
    font-family: $fontfamliy3;
    text-align: justify;
    line-height: 1.7;
    font-size: 14px;
    color: $fontcolorlinks;
  }
  .enter-theOffer {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
  }
  .icon-Marketing {
    height: 30px;
    width: 30px;
    background-color: $color-2;
    color: #fff;
    font-size: 23px;
    border-radius: 50%;
  }
  .Marketing-titel {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    justify-content: center;
    color: $fontcolor;
  }
  .text-featur {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: rgb(97, 97, 97) !important;
    line-height: 1.8;
  }
  .title-featur {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: rgb(33, 33, 33) !important;
  }
  .Marketing-text {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    color: $fontcolor;
  }
  .subtitle {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    font-weight: 600;
    color: $color-2 !important;
    font-size: 17px;
    text-align: center;
    span {
      font-size: 20px;
    }
  }
}
.detail {
  font-family: $fontfamliy3;
  font-size: 15px !important;
}
.price-cat {
  font-family: sans-serif;
  font-size: 16px !important;
  font-weight: 700;
  color: $color-2;
}
.Adv-titel {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 600;
  font-size: 13px;
}
.Adv-text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 400;
  font-size: 13px;
  line-height: 1.8;
  text-align: justify;
}
.text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 500;
  font-size: 20px;

  .v-icon {
    @media (max-width: 600px) {
      font-size: 22px !important;
    }
  }
}
.ToDoList-box {
  @media (max-width: 600px) {
    flex-direction: column;
  }
}
.Store-name {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 500;
  color: $fontcolorlinks !important;
  text-align: center;
}
::v-deep .v-timeline-item__divider {
  min-width: 50px;
}
::v-deep .v-timeline-item__body {
  max-width: calc(100% - 50px) !important;
}
::v-deep .theme--light.v-timeline:before {
  right: 24px !important;
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
.btn {
  position: fixed;
  left: 3px;
  bottom: 51px;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-weight: 600;
  z-index: 5;
  // opacity: 0.7;
}
.container {
  // padding: 0px !important;
}
</style>
