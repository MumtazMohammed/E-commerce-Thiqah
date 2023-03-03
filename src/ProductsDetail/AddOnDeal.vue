<template>
  <div class="DailyOffer my-2">
    <v-container class="pa-0">
      <p class="ma-0 pa-2 d-flex font-weight-bold tital">
        <v-icon size="28" color="yellow darken-3">mdi-fire</v-icon>
        صفقة مع البيعة
      </p>
      <!-- big screen  -->
      <v-row no-gutters class="pa-2 hidden-sm-and-down">
        <v-col cols="2" class="pa-2">
          <v-card flat tile min-height="150">
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="150"
              contain
              class="grey lighten-2"
            >
            </v-img>
            <div class="py-2">
              <v-card-text class="card-text pa-0">
                عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان
                المنبتج عنوان المنبتج
              </v-card-text>
            </div>
          </v-card>
        </v-col>
        <v-icon color="deep-orange">mdi-plus</v-icon>
        <v-col cols="2" class="pa-2" v-for="i in 3" :key="i">
          <v-card flat tile min-height="150">
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="150"
              contain
              class="grey lighten-2"
            >
              <span class="how-many-percent">
                <span style="padding: 0 1px">20</span>%-
              </span>
            </v-img>
            <!-- product title  -->
            <div class="pt-1">
              <v-card-text class="card-text pa-0">
                عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان
                المنبتج عنوان المنبتج
              </v-card-text>
            </div>
            <!-- select product -->
            <div class="">
              <v-row no-gutters align="center">
                <v-checkbox
                  v-model="enabled"
                  hide-details
                  class="shrink mr-0 mt-0"
                  dense
                ></v-checkbox>
                <span class="card-text grey--text pa-0"> حدد الطلب </span>
              </v-row>
            </div>
          </v-card>
        </v-col>
        <!-- See more  -->
        <v-col cols="" class="pa-2 text-end">
          <v-btn
            @click.stop="dialog = true"
            text
            depressed
            class="text-for-all"
          >
            رؤية الكل
          </v-btn>
        </v-col>
        <v-divider vertical></v-divider>
        <!-- <v-spacer></v-spacer> -->
        <v-col cols="2" class="pa-2 col-price">
          <v-card
            class="d-flex flex-column justify-center"
            flat
            tile
            min-height="100%"
          >
            <!-- price total and price befor  -->
            <v-card-text class="pa-1 total-price">
              المجموع :
              <span class="pa-0 befor-price">75 ريال</span>
              <span class="pa-0 after-price">75 ريال</span>
            </v-card-text>
            <!-- save price  -->
            <v-card-text class="pa-1 total-price">
              توفير :
              <span class="pa-0 save-price">75 ريال</span>
            </v-card-text>
            <!-- btn add to cart  -->
            <v-btn depressed class="red text-for-all" dark>
              إضافة إلى السلة
            </v-btn>
          </v-card>
        </v-col>
      </v-row>
      <!-- small screen  -->
      <v-row no-gutters class="pa-2 hidden-md-and-up">
        <v-col cols="4" class="pa-2">
          <v-card rounded="lg" flat class="grey lighten-4" min-height="50">
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="100px"
              class="mx-auto"
            >
            </v-img>
            <div class="text-center">
              <span
                class="font-weight-medium grey--text text-decoration-line-through"
              >
                203 ريال
              </span>
            </div>
            <div class="text-center py-1">
              <span
                class="font-weight-medium font-weight-bold deep-orange--text"
              >
                184 ريال
              </span>
            </div>
          </v-card>
        </v-col>
        <v-icon class="mx-2" color="deep-orange">mdi-plus</v-icon>
        <v-col cols="4" class="pa-2">
          <v-card
            rounded="lg"
            flat
            class="grey lighten-4 overflow-hidden"
            min-height="50"
          >
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="100px"
              class="mx-auto"
            >
              <!-- <span class="how-many-percent"> إضافة الصفقة </span> -->
              <span class="how-many-percent">
                <span style="padding: 0 1px">20</span>%-
              </span>
            </v-img>
            <!-- product title  -->
            <div class="text-center">
              <span
                class="font-weight-medium grey--text text-decoration-line-through"
              >
                203 ريال
              </span>
            </div>
            <div class="text-center py-1">
              <span
                class="font-weight-medium font-weight-bold deep-orange--text"
              >
                184 ريال
              </span>
            </div>
            <!-- select product -->
            <!-- <div class="">
              <v-row no-gutters align="center">
                <v-checkbox
                  v-model="enabled"
                  hide-details
                  class="shrink mr-0 mt-0"
                  dense
                ></v-checkbox>
                <span class="card-text grey--text pa-0"> حدد الطلب </span>
                <v-icon>mdi-menu-down</v-icon>
              </v-row>
            </div> -->
          </v-card>
        </v-col>
        <!-- more btn  -->
        <v-col class="pa-2">
          <v-card
            class="d-flex align-center justify-center"
            flat
            tile
            height="100%"
          >
            <v-card
              @click.stop="dialog = true"
              rounded="lg"
              class="text-center pa-1"
            >
              <v-card-text class="card-text pa-0">
                المزيد
                <span class="mr-1">1</span>
                +
              </v-card-text>
              <v-icon color="deep-orange">mdi-chevron-down</v-icon>
            </v-card>
          </v-card>
        </v-col>
        <!-- price total and price befor  -->
        <v-col cols="12" class="pa-2 col-price">
          <v-row>
            <v-col cols="6">
              <v-card-text class="pa-0 total-price">
                المجموع :
                <span class="pa-0 befor-price">75 ريال</span>
                <span class="pa-0 after-price">75 ريال</span>
              </v-card-text>
              <!-- save price  -->
              <v-card-text class="pa-0 total-price">
                توفير :
                <span class="pa-0 save-price">75 ريال</span>
              </v-card-text>
            </v-col>
            <!-- btn add to cart  -->
            <v-col cols="6" class="mt-auto text-end">
              <v-btn small depressed dark class="red darken-1 text-for-all">
                إضافة الى السلة
              </v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
      <!--  -->
      <v-dialog
        class="rounded-0"
        persistent
        no-click-animation
        v-model="dialog"
        width="1000"
      >
        <v-toolbar fixed>
          <v-toolbar-title>
            المحدد
            <span class="mr-2">
              <span class="deep-orange--text">0</span> /
              {{ getCarInfo.length }}
            </span>
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-btn depressed dark class="red darken-1 text-for-all">
            إضافة الى السلة
          </v-btn>
          <v-btn @click="dialog = false" icon class="mr-2">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-toolbar>
        <v-card flat tile height="590" color="grey lighten-2 overflow-y-auto">
          <v-row no-gutters>
            <v-col
              cols="12"
              v-for="(Product, index) in getCarInfo"
              :key="index"
              class="pa-1"
            >
              <v-card
                width="100%"
                style="overflow: hidden; background-color: #fff"
                flat
              >
                <v-row no-gutters align="center">
                  <!-- select product -->
                  <v-checkbox
                    v-model="enabled"
                    hide-details
                    class="shrink mr-2 mt-0"
                    dense
                  ></v-checkbox>
                  <!-- Product Img and name  -->
                  <v-col cols="8" md="6" lg="6" sm="6">
                    <v-row no-gutters align="center">
                      <a
                        router-link
                        :to="{
                          name: 'ShowTheProduct',
                          params: {
                            carName: Product.name,
                            carShape: Product.Shape,
                            carId: Product.id,
                            Company: Product.folder,
                          },
                        }"
                      >
                        <v-img
                          width="130"
                          height="100"
                          contain
                          :src="getimageUrl(Product.folder, Product.image)"
                        ></v-img>
                      </a>
                      <v-col>
                        <v-card-text
                          :to="{
                            name: 'ShowTheProduct',
                            params: {
                              carName: Product.name,
                              carShape: Product.Shape,
                              carId: Product.id,
                              Company: Product.folder,
                            },
                          }"
                          style="
                            display: -webkit-box;
                            -webkit-line-clamp: 2;
                            -webkit-box-orient: vertical;
                            overflow: hidden;
                          "
                          class="card-text py-1 pb-0 pa-2"
                        >
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }} {{ Product.company }}
                          {{ Product.name }}
                          {{ Product.company }}
                        </v-card-text>
                      </v-col>
                    </v-row>
                  </v-col>
                  <v-col>
                    <v-card-actions class="justify-center pa-0">
                      <v-btn depressed text class="text-for-all" color="grey darken-2">
                        تحديد الطلب
                        <v-icon>mdi-menu-down</v-icon>
                      </v-btn>
                    </v-card-actions>
                  </v-col>
                  <v-col cols="">
                    <!-- Product price -->
                    <strong
                      class="PriceAfter pb-0 grey--text text-decoration-line-through text-center py-1 pa-2 text-truncate"
                    >
                      {{ Product.payment }}
                      <small class="text-truncate">ريال</small>
                    </strong>
                    <strong
                      class="PriceAfter pt-0 red--text py-1 pa-2 text-center text-truncate"
                    >
                      {{ Product.payment }}
                      <small class="text-truncate">ريال</small>
                    </strong>
                  </v-col>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-card>
      </v-dialog>
    </v-container>
  </div>
</template>
<script>
import VerifiedCar from "../data-json/All-Car.json";
export default {
  name: "SameWonerProducts",
  components: {},
  data() {
    return {
      dialog: false,
      VerifiedCar,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetCarVerified = [];
      for (let i = 0; i < this.VerifiedCar.length; i++) {
        if (this.VerifiedCar[i].Vip == true) {
          GetCarVerified.push(this.VerifiedCar[i]);
        }
      }
      return GetCarVerified;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.DailyOffer {
  width: 100%;
  min-height: 20vh;
  background-color: #fff;
  .card-text {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    // color: $fontcolor !important;
  }
  .text-for-all {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
  }
  .tital {
    font-family: $fontfamliy3;
    font-size: 22px;
    color: $color-2;
    pointer-events: none;

    @media (max-width: 470px) {
      font-size: 18px;
    }
    @media (max-width: 350px) {
      font-size: 17px;
    }
  }
}
.text-for-all {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 14px;
}
.how-many-percent {
  position: absolute;
  top: 0;
  right: 0;
  clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 25% 100%, 0% 50%);
  background-color: #ef5350;
  padding: 0px 3px 0px 8px;
  color: white;
  @media (max-width: 960px) {
    // clip-path: none !important;
    font-size: 12px !important;
    // padding: 0px 2px !important;
    // border-radius: 3px !important;
  }
}
.befor-price {
  font-family: sans-serif !important;
  font-size: 13px;
  font-weight: 700;
  margin: 0 2px;
  text-decoration: line-through;
  color: grey !important;
}
.after-price {
  font-family: sans-serif !important;
  font-size: 13.5px;
  font-weight: 700;
  margin: 0 2px;
  color: $fontcolor !important;
}
.save-price {
  font-family: sans-serif !important;
  font-size: 13.5px;
  font-weight: 700;
  margin: 0 2px;
  color: $color-2 !important;
}
.total-price {
  font-family: $fontfamliy3 !important;
  font-size: 15px;
  color: $fontcolor !important;
  pointer-events: none;
}
.befor-price {
  font-family: sans-serif !important;
  font-size: 13px;
  font-weight: 700;
  margin: 0 2px;
  text-decoration: line-through;
  color: grey !important;
}
.after-price {
  font-family: sans-serif !important;
  font-size: 13.5px;
  font-weight: 700;
  margin: 0 2px;
  color: $fontcolor !important;
}
::v-deep .col-price.pa-2.col.col-2 {
  flex: 0 0 18%;
  max-width: 18%;
}
// Products
.card-text {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 14px;
  color: $fontcolor !important;
}

.PriceAfter {
  font-size: 17px !important;
  display: block !important;
  // color: $color-2;
  font-weight: 600 !important;
  font-family: sans-serif !important;
}

::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
  // height: 95% !important;
  border-radius: 0 !important;
}
</style>
