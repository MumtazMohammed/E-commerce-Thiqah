<template>
  <div class="DailyOffer my-2">
    <v-container class="pa-0">
      <p class="ma-0 pa-2 d-flex font-weight-bold tital">
        <v-icon size="28" color="yellow darken-3">mdi-fire</v-icon>
        صفقة مع المنتج
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
            <!-- product title  -->
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
        <v-spacer></v-spacer>
        <v-divider vertical></v-divider>
        <v-spacer></v-spacer>
        <v-col cols="2" class="pa-2 col-price">
          <v-card
            class="d-flex flex-column align-center justify-center"
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
            <v-card-text class="pa-1 total-price">
              توفير :
              <span class="pa-0 save-price">75 ريال</span>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <!-- small screen  -->
      <v-row no-gutters class="pa-2 hidden-md-and-up">
        <v-col cols="4" class="pa-2">
          <v-card flat min-height="150">
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="100"
              contain
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
        <v-icon class="mx-2" color="deep-orange">mdi-plus</v-icon>
        <v-col cols="4" class="pa-2">
          <v-card flat min-height="150">
            <v-img
              src="https://picsum.photos/500/300?image"
              lazy-src="https://picsum.photos/10/6?image"
              height="100"
              contain
            >
              <span class="how-many-percent"> إضافة الصفقة </span>
            </v-img>
            <!-- product title  -->
            <div class="pt-1">
              <v-card-text class="card-text pa-0">
                عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان المنبتج عنوان
                المنبتج عنوان المنبتج
              </v-card-text>
            </div>
          </v-card>
        </v-col>
        <v-col cols="2" class="pa-2 mr-2">
          <v-card
            class="d-flex align-center justify-center"
            flat
            tile
            height="100%"
          >
            <!-- more btn  -->
            <div class="text-center">
              <v-card-text class="card-text pa-0"> المزيد </v-card-text>
              <v-icon color="grey">mdi-chevron-down</v-icon>
            </div>
          </v-card>
        </v-col>
        <v-col cols="12" class="pa-2 col-price">
          <v-row>
            <v-col cols="6">
              <!-- price total and price befor  -->
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
            <v-col cols="6" class="my-auto text-end">
              <v-btn small depressed dark class="red darken-1 text-for-all">
                إضافة الى السلة
              </v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "SameWonerProducts",
  components: {},
  data() {
    return {};
  },
  // this is help full to call the image inside folder and inject to the src
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
  .how-many-percent {
    position: absolute;
    top: 0;
    right: 0;
    clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 25% 100%, 0% 50%);
    background-color: #ef5350;
    padding: 0px 3px 0px 8px;
    color: white;
    @media (max-width: 960px) {
      clip-path: none !important;
      font-size: 12px !important;
      padding: 0px 2px !important;
      border-radius: 3px !important;
    }
  }
  .total-price {
    font-family: $fontfamliy3;
    font-size: 15px;
    color: $fontcolor !important;
    pointer-events: none;
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
  }
}
::v-deep .col-price.pa-2.col.col-2 {
  flex: 0 0 18%;
  max-width: 18%;
}
</style>
