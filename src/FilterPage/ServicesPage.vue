<template>
  <div class="Products">
    <TheNavBar />
    <v-container class="px-0">
      <!-- fillter big screen from 600px and up -->
      <v-card flat class="grey lighten-2 hidden-xs-only">
        <v-card-actions class="pa-2">
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
          <v-select
            dense
            class="mx-1"
            hide-details
            flat
            :items="items"
            placeholder="ترتيب حسب المنطقة"
            solo
          ></v-select>
        </v-card-actions>
      </v-card>
      <!-- fillter small screen from 600px and down -->
      <div class="hidden-sm-and-up filtertion">
        <v-dialog
          no-click-animation
          v-model="filterdialog"
          persistent
          max-width="360"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="filtertion-btn"
              class="primary filtertion-btn"
              dark
              icon
              v-bind="attrs"
              v-on="on"
              elevation="8"
              width="52"
              height="52"
            >
              <v-icon>mdi-filter</v-icon>
            </v-btn>
          </template>
          <v-card class="grey lighten-2 pa-2">
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-select
              dense
              class="ma-2"
              hide-details
              flat
              :items="items"
              placeholder="ترتيب حسب المنطقة"
              solo
            ></v-select>
            <v-card-actions class="pa-0">
              <v-btn
                color="green "
                class="btn"
                text
                small
                @click="filterdialog = false"
              >
                عرض
              </v-btn>
              <v-spacer></v-spacer>
              <v-btn
                color="red darken-1 "
                class="btn"
                text
                small
                @click="filterdialog = false"
              >
                إلغاء
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
      <v-row no-gutters class="mt-2">
        <v-col
          cols="6"
          md="2"
          sm="6"
          lg="2"
          xl="2"
          class="pa-2"
          v-for="(Product, i) in Products"
          :key="i"
        >
          <div style="position: relative">
            <h1 class="ribbon">متميز</h1>
            <v-card
              :to="{
                name: 'ShowTheProduct',
                params: {
                  carName: Product.name,
                  carShape: Product.Shape,
                  carId: Product.id,
                  Company: Product.folder,
                },
              }"
              min-height="220px"
              width="100%"
              flat
              tile
              color="transparent"
            >
              <div v-if="Product.discountPercent" class="best-price-tag">
                <small class="discountPercent">
                  {{ Product.discountPercent }}-
                </small>
              </div>
              <v-img
                height="170"
                full-width
                :src="getimageUrl(Product.folder, Product.image)"
              ></v-img>
              <v-card-text
                class="d-inline-block card-text py-0 pa-2 text-truncate"
              >
                {{ Product.name }} {{ Product.company }}
              </v-card-text>
              <v-card-actions class="py-0 justify-space-between">
                <strong
                  class="grey--text text--lighten-1 PriceBefore text-truncate"
                >
                  {{ Product.payment }}
                  <small class="text-truncate">ريال</small>
                </strong>
                <strong class="PriceAfter text-truncate">
                  {{ Product.payment }}
                  <small class="text-truncate">ريال</small>
                </strong>
              </v-card-actions>
              <v-card-actions class="py-1 justify-space-between">
                <p class="ma-0 sold-info px-2 text-truncate">
                  <span>{{ Product.id }} </span>بيعت
                </p>
                <span class="card-text grey--text px-2">
                  {{ Product.location }}
                </span>
              </v-card-actions>
            </v-card>
          </div>
        </v-col>
        <v-col cols="12" class="mt-2">
          <v-card-actions class="justify-center">
            <v-btn elevation="0" width="190" class="seeMoreBtn">
              المزيد
              <v-icon right size="16">mdi-dots-horizontal</v-icon>
            </v-btn>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Products from "../data-json/All-Car.json";
import TheNavBar from "../NavBar/TheNavBar.vue";
export default {
  name: "ServicesPage",
  components: { TheNavBar },
  data() {
    return {
      Products,
      filterdialog: null,
      items: ["مقديشو", "كزبرا", "صلصة", "ثوم"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // computed: {
  //   getCarInfo() {
  //     let GetShowroomfeatured = [];
  //     for (let i = 0; i < this.featuredshowrooms.length; i++) {
  //       if (this.featuredshowrooms[i].featured == true) {
  //         GetShowroomfeatured.push(this.featuredshowrooms[i]);
  //       }
  //     }
  //     return GetShowroomfeatured;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Products {
  width: 100%;
  min-height: 70vh;
  background-color: $color-background;
  .seeMoreBtn {
    letter-spacing: 0 !important;
    font-size: 16px;
    font-family: $fontfamliy3;
    color: $color-2;
    background-color: #ffffff !important;
  }
}
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor;
  letter-spacing: 0 !important;
  font-size: 13px !important;
}
.sold-info {
  font-family: $fontfamliy3 !important;
  font-size: 13px !important;
  font-weight: 600 !important;
  color: $fontcolorlinks;
  span {
    color: $color-2 !important;
    margin-left: 5px;
    font-size: 14px !important;
    letter-spacing: 1.5px !important;
  }
}
.PriceBefore {
  font-size: 14px !important;
  text-decoration: line-through;
}
.PriceAfter {
  font-size: 15px !important;
  color: $color-2;
}
::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
}
::v-deep .v-select__selection.v-select__selection--comma {
  font-family: $fontfamliy3;
  font-size: 14px;
  letter-spacing: 0;
}
::v-deep .v-list-item__title {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
::v-deep input {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}
::v-deep .v-menu__content.theme--light.menuable__content__active {
  z-index: 15 !important;
}
.filtertion {
  position: fixed;
  z-index: 6;
  left: 8px;
  bottom: 46px;
}
.filtertion-btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
  transform: scale(0.8);
}
.btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3;
}
.best-price-tag {
  position: absolute;
  left: 4px;
  top: 0px;
  clip-path: polygon(
    50% 0%,
    100% 0,
    100% 35%,
    100% 70%,
    100% 100%,
    49% 70%,
    0 100%,
    0% 70%,
    0% 35%,
    0 0
  );

  background-color: $color-2;
  width: 35px;
  height: 40px;
  display: flex;
  justify-content: center;
  // transform: rotate(360deg);
  z-index: 5;
  border-radius: 0 !important;
}
.discountPercent {
  color: white !important;
  font-weight: 500;
  font-size: 13px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}
.ribbon {
  position: absolute;
  top: 3px;
  right: 0px;
  z-index: 5;
  padding: 0 5px;
  width: 50px;
  text-align: center;
  font-size: 11px;
  color: #ffffff;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  border-radius: 5px 0px 0px 5px !important;
  background: $color-2;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
}
.ribbon:before {
  content: "";
  position: absolute;
  display: block;
  width: 0.5em;
  height: 100%;
  padding: 0 0 20px 0px !important;
  top: 0;
  right: -0.51em;
  background: inherit;
  border-radius: 0px 5px 5px 0px !important;
}

.ribbon:after {
  position: absolute;
  content: "";
  display: block;
  width: 0.313em;
  height: 0.313em;
  background: rgba(0, 0, 0, 0.35);
  bottom: -0.313em;
  right: -0.3em;
  border-radius: 0px 5px 5px 0px !important;
  box-shadow: inset -1px 2px 2px rgba(0, 0, 0, 0.3);
}
</style>
