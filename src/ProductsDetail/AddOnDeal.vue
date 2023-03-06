<template>
  <div class="DailyOffer my-2">
    <v-container class="pa-0">
      <p class="ma-0 pa-2 d-flex font-weight-bold tital">
        <v-icon right size="28" color="amber accent-1">mdi-tag</v-icon>
        صفقة مع البيعة
      </p>
      <v-sheet
        :height="SeeMore ? `auto` : `212`"
        class="overflow-y-hidden hidden-xs-only"
      >
        <v-row no-gutters align="center" justify="center" class="pa-2">
          <v-col cols="12" class="pa-2 py-1">
            <v-card
              flat
              class="grey lighten-4"
              width="100%"
              style="overflow: hidden"
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
                <v-col cols="8" md="5" lg="5" sm="6">
                  <v-row no-gutters align="center">
                    <v-avatar tile size="80" color="red">
                      <v-img
                        src="https://picsum.photos/500/300?image"
                        lazy-src="https://picsum.photos/500/300?image"
                      >
                      </v-img>
                    </v-avatar>
                    <v-col>
                      <v-card-text
                        style="
                          display: -webkit-box;
                          -webkit-line-clamp: 2;
                          -webkit-box-orient: vertical;
                          overflow: hidden;
                        "
                        class="card-text py-1 pb-0 pa-2"
                      >
                        ، من المهم أن يكون الموقع جاذبا من الناحية البصرية
                      </v-card-text>
                    </v-col>
                  </v-row>
                </v-col>
                <v-col>
                  <v-card-actions class="justify-center pa-0">
                    <v-btn
                      depressed
                      text
                      class="text-for-all"
                      color="grey darken-2"
                    >
                      تحديد الطلب
                      <v-icon>mdi-menu-down</v-icon>
                    </v-btn>
                  </v-card-actions>
                </v-col>
                <v-col>
                  <!-- Product price -->
                  <strong
                    class="d-block pb-0 grey--text text-decoration-line-through text-center py-1 pa-2 text-truncate"
                  >
                    120
                    <small class="text-truncate">ريال</small>
                  </strong>
                  <strong
                    style="color: #fc624d"
                    class="d-block pt-0 py-1 pa-2 text-center text-truncate"
                  >
                    110
                    <small class="text-truncate">ريال</small>
                  </strong>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <v-icon color="deep-orange">mdi-plus</v-icon>
          <v-col
            cols="12"
            v-for="(Product, index) in getCarInfo"
            :key="index"
            class="pa-2 py-1"
          >
            <v-card
              width="100%"
              style="overflow: hidden"
              class="grey lighten-4"
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
                <v-col cols="10" md="5" lg="5" sm="6">
                  <v-row no-gutters align="center">
                    <v-avatar tile size="80" color="red">
                      <v-img
                        :src="getimageUrl(Product.folder, Product.image)"
                        :lazy-src="getimageUrl(Product.folder, Product.image)"
                      >
                        <span class="how-many-percent">%20</span>
                      </v-img>
                    </v-avatar>
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
                    <v-btn
                      depressed
                      text
                      class="text-for-all"
                      color="grey darken-2"
                    >
                      تحديد الطلب
                      <v-icon>mdi-menu-down</v-icon>
                    </v-btn>
                  </v-card-actions>
                </v-col>
                <v-col>
                  <!-- Product price -->
                  <strong
                    class="d-block pb-0 grey--text text-decoration-line-through text-center py-1 pa-2 text-truncate"
                  >
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                  <strong
                    style="color: #fc624d"
                    class="d-block pt-0 py-1 pa-2 text-center text-truncate"
                  >
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <!-- <v-spacer></v-spacer> -->
        </v-row>
      </v-sheet>
      <v-sheet
        :height="SeeMore ? `auto` : `244`"
        class="overflow-y-hidden hidden-sm-and-up"
      >
        <v-row no-gutters align="center" justify="center" class="pa-2">
          <v-col cols="12" class="pa-2 py-1">
            <v-card
              flat
              class="grey lighten-4"
              width="100%"
              style="overflow: hidden"
            >
              <v-row no-gutters align="center">
                <v-col>
                  <v-row
                    style="flex-direction: column !important"
                    justify="center"
                    align="center"
                    no-gutters
                  >
                    <!-- Product Img and name  -->
                    <v-avatar tile size="70" color="red">
                      <v-img
                        src="https://picsum.photos/500/300?image"
                        lazy-src="https://picsum.photos/500/300?image"
                      >
                      </v-img>
                    </v-avatar>
                    <!-- select product -->
                    <v-checkbox
                      v-model="enabled"
                      hide-details
                      class="shrink mt-0"
                      dense
                    ></v-checkbox>
                  </v-row>
                </v-col>
                <v-col cols="9">
                  <v-card-text
                    style="
                      display: -webkit-box;
                      -webkit-line-clamp: 2;
                      -webkit-box-orient: vertical;
                      overflow: hidden;
                    "
                    class="card-text px-2 pa-0"
                  >
                    من المهم أن يكون الموقع جاذبا من الناحية البصرية من المهم أن
                    يكون الموقع جاذبا من الناحية البصرية من المهم أن يكون الموقع
                    جاذبا من الناحية البصرية من المهم أن يكون الموقع جاذبا من
                    الناحية البصرية
                  </v-card-text>
                  <v-card-actions class="justify-space-between pa-0">
                    <v-btn
                      depressed
                      text
                      class="text-for-all"
                      color="grey darken-2"
                    >
                      تحديد الطلب
                      <v-icon>mdi-menu-down</v-icon>
                    </v-btn>
                    <!-- Product price -->
                    <div>
                      <strong
                        class="d-block pb-0 grey--text text-decoration-line-through text-center py-1 pa-2 text-truncate"
                      >
                        120
                        <small class="text-truncate">ريال</small>
                      </strong>
                      <strong
                        style="color: #fc624d"
                        class="d-block pt-0 py-1 pa-2 text-center text-truncate"
                      >
                        110
                        <small class="text-truncate">ريال</small>
                      </strong>
                    </div>
                  </v-card-actions>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <v-icon color="deep-orange">mdi-plus</v-icon>
          <v-col
            cols="12"
            v-for="(Product, index) in getCarInfo"
            :key="index"
            class="pa-2 py-1"
          >
            <v-card
              width="100%"
              style="overflow: hidden"
              class="grey lighten-4"
              flat
            >
              <v-row no-gutters>
                <v-col>
                  <v-row
                    style="flex-direction: column !important"
                    justify="center"
                    no-gutters
                    align="center"
                  >
                    <!-- Product Img and name  -->
                    <v-avatar tile size="70" color="red">
                      <v-img
                        :src="getimageUrl(Product.folder, Product.image)"
                        :lazy-src="getimageUrl(Product.folder, Product.image)"
                      >
                        <span class="how-many-percent">%20</span>
                      </v-img>
                    </v-avatar>
                    <!-- select product -->
                    <v-checkbox
                      v-model="enabled"
                      hide-details
                      class="ma-0"
                      dense
                    ></v-checkbox>
                  </v-row>
                </v-col>
                <v-col cols="9">
                  <v-card-text
                    style="
                      display: -webkit-box;
                      -webkit-line-clamp: 2;
                      -webkit-box-orient: vertical;
                      overflow: hidden;
                    "
                    class="card-text px-2 pa-0"
                  >
                    {{ Product.name }} {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                    {{ Product.company }}
                    {{ Product.name }}
                    {{ Product.company }}
                  </v-card-text>
                  <v-card-actions class="justify-space-between pa-0">
                    <v-btn
                      depressed
                      text
                      class="text-for-all"
                      color="grey darken-2"
                    >
                      تحديد الطلب
                      <v-icon>mdi-menu-down</v-icon>
                    </v-btn>
                    <!-- Product price -->
                    <div>
                      <strong
                        class="d-block pb-0 grey--text text-decoration-line-through text-center py-1 pa-2 text-truncate"
                      >
                        {{ Product.payment }}
                        <small class="text-truncate">ريال</small>
                      </strong>
                      <strong
                        style="color: #fc624d"
                        class="d-block pt-0 py-1 pa-2 text-center text-truncate"
                      >
                        {{ Product.payment }}
                        <small class="text-truncate">ريال</small>
                      </strong>
                    </div>
                  </v-card-actions>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <!-- <v-spacer></v-spacer> -->
        </v-row>
      </v-sheet>
      <!-- see more btn  -->
      <v-col class="text-center pa-0">
        <a
          v-if="!SeeMore"
          class="text-for-all grey--text text--darken-2"
          @click="SeeMore = !SeeMore"
        >
          رؤية المزيد (<span>{{ VerifiedCar.length }}</span
          >)
        </a>
        <a
          v-else
          class="text-for-all grey--text text--darken-2"
          @click="SeeMore = !SeeMore"
        >
          رؤية أقل
        </a>
      </v-col>
      <!-- total price and how much u save  -->
      <v-col cols="12" class="pa-2 col-price">
        <v-row no-gutters align="center">
          <v-col class="pa-2 col-price">
            <!-- price total and price befor  -->
            <v-card-text class="pa-1 total-price">
              المجموع :
              <span class="pa-0 after-price">75 ريال</span>
            </v-card-text>
            <!-- save price  -->
            <v-card-text class="pa-1 total-price">
              موفر :
              <span class="pa-0 save-price">75 ريال</span>
            </v-card-text>
          </v-col>
          <!-- btn add to cart  -->
          <v-btn depressed class="red text-for-all" dark>
            إضافة إلى السلة
          </v-btn>
        </v-row>
      </v-col>
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
      SeeMore: false,
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
  overflow: hidden;
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
  span {
    font-family: sans-serif;
    color: $color-2;
  }
}
.how-many-percent {
  position: absolute;
  top: 0;
  right: 0;
  clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 25% 100%, 0% 50%);
  background-color: #ef5350;
  padding: 0px 3px 0px 8px;
  color: white;
  font-size: 14px !important;
  @media (max-width: 600px) {
    // clip-path: none !important;
    font-size: 13px !important;
    // padding: 0px 2px !important;
    // border-radius: 3px !important;
  }
}
.befor-price {
  font-family: sans-serif !important;
  font-size: 14px !important;
  font-weight: 700;
  margin: 0 2px;
  text-decoration: line-through;
  color: grey !important;
}
.after-price {
  font-family: sans-serif !important;
  font-size: 17px !important;
  font-weight: 700 !important;
  margin: 0 2px;
  color: $fontcolor !important;
}
.save-price {
  font-family: sans-serif !important;
  font-size: 17px !important;
  font-weight: 700 !important;
  margin: 0 2px;
  color: $color-2 !important;
}
.total-price {
  font-family: $fontfamliy3 !important;
  font-size: 16px;
  color: $fontcolor !important;
  pointer-events: none;
  display: block;
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

::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
  // height: 95% !important;
  border-radius: 0 !important;
}
::v-deep .v-input--selection-controls__input {
  margin: 0px !important;
}
</style>
