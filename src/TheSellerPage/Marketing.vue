<template>
  <div class="Marketing">
    <!-- small Screen Tabs  -->
    <div class="hidden-md-and-up">
      <v-app-bar flat fixed color="#fc624d" dark>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-home </v-icon>
        </v-btn>
        <v-toolbar-title class="pr-1 titel">الرئيسية</v-toolbar-title>
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
    <v-container class="">
      <v-sheet>
        <v-card-title class="welcom-text">
          مرحباً بك في مركز التسويق والعروضات
        </v-card-title>
        <v-chip-group
          v-model="selection"
          active-class="blue--text text--accent-4"
          mandatory
        >
          <v-chip outlined @click="window = 0"> الخصومات </v-chip>
          <v-chip outlined @click="window = 1"> القسائم </v-chip>
        </v-chip-group>
        <v-window v-model="window">
          <v-window-item class="" style="min-height: 100vh" :value="0">
            <v-row no-gutters>
              <v-col cols="12" class="pa-2">
                <v-text-field
                  class="pa-0"
                  v-model="search"
                  placeholder="  أبحث عن أسم المنتج ؟ "
                  hide-details="true"
                  append-icon="mdi-magnify"
                  @focus="ShowSerachCardvisble = true"
                ></v-text-field>
              </v-col>
              <v-col
                v-for="(Car, i) in ShowRoomUserCars"
                :key="i"
                cols="6"
                sm="4"
                md="3"
                lg="2"
                class="pa-2"
              >
                <v-dialog no-click-animation persistent width="400">
                  <template v-slot:activator="{ on, attrs }">
                    <v-card
                      v-bind="attrs"
                      v-on="on"
                      max-height="700"
                      class="overflow-hidden"
                      outlined
                    >
                      <!-- Products main Img  -->
                      <v-img
                        fullscreen
                        height="130"
                        class="grey darken-4"
                        :src="getimageUrl(Car.folder, Car.image)"
                        :lazy-src="getimageUrl(Car.folder, Car.image)"
                        alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                      ></v-img>
                      <!-- Products detail -->
                      <v-card-text class="detail pa-1 text-truncate">
                        <span>{{ Car.company }} {{ Car.name }}</span>
                      </v-card-text>
                      <v-card-text class="price justify-center pa-0">
                        {{ Car.payment }}
                        <span class="grey--text text--darken-3">ريال</span>
                      </v-card-text>
                      <v-card-actions class="pa-2">
                        <v-card-text class="text pa-0 grey--text">
                          في المخزون
                        </v-card-text>
                        <span class="cat text-end pa-0"> 457 </span>
                      </v-card-actions>
                    </v-card>
                  </template>
                  <!-- set the offer price  -->
                  <template v-slot:default="dialog">
                    <v-card min-height="300">
                      <v-carousel
                        height="210px"
                        width="100%"
                        touch
                        hide-delimiters
                        class="overflow--hidden"
                      >
                        <v-carousel-item
                          v-for="(singleImage, x) in Car.images"
                          :key="x"
                        >
                          <v-img
                            class="grey darken-3"
                            aspect-ratio="1.9"
                            contain
                            :src="getimageUrl(Car.folder, singleImage)"
                          >
                          </v-img>
                        </v-carousel-item>
                      </v-carousel>
                      <div>
                        <v-card-title class="detail pa-2 text-truncate">
                          <span>{{ Car.company }} {{ Car.name }}</span>
                          <v-spacer></v-spacer>
                        </v-card-title>
                        <v-row class="px-2" align="center" no-gutters>
                          <span class="stocked">
                            في المخزن
                            <span class="mx-2 red--text">{{ Car.id }} </span>
                          </span>
                          <v-spacer></v-spacer>
                          <span class="price">
                            {{ Car.payment }}
                          </span>
                        </v-row>
                        <v-sheet width="90%" class="mx-auto">
                          <v-select
                            :items="items"
                            placeholder="أختار نوع العرض"
                            persistent-hint
                          ></v-select>
                        </v-sheet>
                        <v-card flat class="my-1">
                          <span class="disc-text"> قيمة الخصم </span>
                          <v-text-field
                            hide-details
                            solo-inverted
                            dense
                            tile
                            flat
                            class="mx-3"
                            v-model="offer"
                          >
                          </v-text-field>
                        </v-card>
                        <v-card flat class="my-1">
                          <span class="disc-text"> الكمية</span>
                          <v-text-field
                            hide-details
                            solo-inverted
                            dense
                            flat
                            class="mx-3"
                            v-model="offer"
                          >
                          </v-text-field>
                        </v-card>
                      </div>
                      <v-divider></v-divider>
                      <v-card-actions>
                        <v-btn
                          outlined
                          class="btn"
                          text
                          @click="dialog.value = false"
                        >
                          نشر العرض
                        </v-btn>
                        <v-spacer></v-spacer>
                        <v-btn
                          outlined
                          class="btn"
                          text
                          @click="dialog.value = false"
                        >
                          إلغاء
                        </v-btn>
                      </v-card-actions>
                    </v-card>
                  </template>
                </v-dialog>
              </v-col>
            </v-row>
          </v-window-item>
          <v-window-item class="" style="min-height: 100vh" :value="1">
            <v-row no-gutters>
              <v-col cols="12" class="pa-2">
                <v-card-title class="justify-center welcom-text">
                  أختر نوع القسيمة
                </v-card-title>
              </v-col>
              <v-col cols="12" class="pa-2">
                <v-card
                  width="350"
                  flat
                  style="border: 2px dashed #ffd54f !important"
                  color="amber lighten-5"
                  class="mx-auto"
                >
                  <v-row no-gutters>
                    <v-col>
                      <v-card-subtitle class="text pa-0 pr-1">
                        خصم <span class="mx-1"><span>20</span>%</span>
                      </v-card-subtitle>
                      <v-card-text class="pa-0 pr-1 text">
                        أنفق
                        <span class="mx-1">
                          52<v-icon size="17">mdi-currency-rial</v-icon>
                        </span>
                        كحد أدنى
                      </v-card-text>
                      <v-card-text class="pa-0 pr-1 text">
                        متاح حتى
                        <span>10/2/2020</span>
                      </v-card-text>
                    </v-col>
                    <v-col style="margin: auto 0; text-align: center" cols="3">
                      <v-btn
                        small
                        dark
                        class="deep-orange btn lighten-1"
                        elevation="0"
                      >
                        أخذ
                      </v-btn>
                    </v-col>
                  </v-row>
                </v-card>
              </v-col>
              <v-col cols="12" class="pa-2">
                <v-card
                  width="350"
                  flat
                  style="border: 2px dashed #ffd54f !important"
                  color="amber lighten-5"
                  class="mx-auto"
                >
                  <v-row no-gutters>
                    <v-col>
                      <v-card-subtitle class="text pa-0 pr-1">
                        خصم <span class="mx-1"><span>20</span>%</span>
                      </v-card-subtitle>
                      <v-card-text class="pa-0 pr-1 text">
                        أنفق
                        <span class="mx-1">
                          52<v-icon size="17">mdi-currency-rial</v-icon>
                        </span>
                        كحد أدنى
                      </v-card-text>
                      <v-card-text class="pa-0 pr-1 text">
                        متاح حتى
                        <span>10/2/2020</span>
                      </v-card-text>
                    </v-col>
                    <v-col style="margin: auto 0; text-align: center" cols="3">
                      <v-btn
                        small
                        dark
                        class="deep-orange btn lighten-1"
                        elevation="0"
                      >
                        أخذ
                      </v-btn>
                    </v-col>
                  </v-row>
                </v-card>
              </v-col>
            </v-row>
          </v-window-item>
        </v-window>
      </v-sheet>
    </v-container>
  </div>
</template>
<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
export default {
  name: "Marketing",
  data() {
    return {
      dialog: false,
      toggle_exclusive: undefined,
      neighborhoods: [],
      ShowRoomUserCars,
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      offer: 0,
      selection: 0,
      window: 0,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
    reset() {
      return (this.search = "");
    },
    decrement() {
      this.offer--;
    },
    increment() {
      this.offer++;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Marketing {
  width: 100%;
  min-height: 100vh;
  font-family: $fontfamliy3 !important;

  .welcom-text {
    font-family: $fontfamliy3;
    color: grey;
    letter-spacing: 0px;
    @media (max-width: 800px) {
      font-size: 17px;
    }
  }
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  font-family: $fontfamliy3;
  font-weight: 600;
  font-size: 14px;
  // height: 18px;
  color: $fontcolorlinks;
  text-align: center;
}
::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
}
.detail {
  font-family: $fontfamliy3;
  font-weight: 600;
  font-size: 15px !important;
}
.price {
  font-family: sans-serif !important;
  font-weight: 700 !important;
  font-size: 19px !important;
  display: flex;
  color: $color-2 !important;
  span {
    font-size: 13px !important;
    margin-right: 2px;
  }
}
.btn {
  font-family: $fontfamliy3;
  font-weight: 500;
  font-size: 15px !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
}
.stocked {
  font-family: sans-serif;
  font-size: 16px;
  font-weight: 700;
}

.cat {
  font-family: $fontfamliy3;
  font-weight: 500;
  font-size: 13px !important;
  @media (max-width: 600px) {
    font-size: 13px !important;
    padding: 10px !important;
  }
}
.disc-text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px;
  padding: 5px;
  display: block;
  text-align: center;
}
.chip {
  // border-color: $color-2 !important;
  font-size: 14px !important;
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  // font-weight: 600;
}
Voucher .text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
}
.btn {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolor !important;
  font-size: 14px !important;
  font-weight: 600 !important;
  padding: 0 6px !important ;
  min-width: 50px !important;
}
.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
</style>
