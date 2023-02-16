<template>
  <div class="Products">
    <TheNavBar />
    <v-container class="pt-0">
      <v-sheet
        style="height: calc(100vh - 106px); overflow-y: auto"
        class="hidden-md-and-up"
      >
        <v-banner style="z-index: 2" class="pa-0" sticky>
          <FilterSearch />
        </v-banner>
        <v-row no-gutters>
          <v-col
            cols="6"
            md="2"
            sm="3"
            lg="2"
            class="pa-2"
            v-for="Product in Products"
            :key="Product.id"
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
                style="
                  overflow: hidden;
                  background-color: transparent;
                  position: relative;
                "
                color=""
                outlined
              >
                <div v-if="Product.discountPercent" class="best-price-tag">
                  <small class="discountPercent">
                    {{ Product.discountPercent }}-
                  </small>
                </div>
                <v-img
                  height="130"
                  :src="getimageUrl(Product.folder, Product.image)"
                ></v-img>
                <v-card-text
                  class="d-inline-block card-text py-1 pa-2 text-truncate"
                >
                  {{ Product.name }} {{ Product.company }}
                </v-card-text>
                <v-card-actions class="py-0 justify-center">
                  <strong class="PriceAfter text-truncate">
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                </v-card-actions>
                <v-card-actions class="py-1 justify-space-between">
                  <p class="ma-0 sold-info text-truncate">
                    <span>{{ Product.id }} </span>بيعت
                  </p>
                  <span class="sold-info">
                    {{ Product.location }}
                  </span>
                </v-card-actions>
              </v-card>
            </div>
          </v-col>
        </v-row>
      </v-sheet>
      <v-sheet
        v-scroll.self="onScroll"
        max-height="100vh"
        class="transparent overflow-y-auto py-2 hidden-sm-and-down"
      >
        <v-row no-gutters>
          <v-col cols="3">
            <v-banner class="pa-0" sticky>
              <FilterSearch />
            </v-banner>
          </v-col>
          <v-col cols="9">
            <v-row no-gutters>
              <v-col
                cols="6"
                md="3"
                sm="4"
                lg="3"
                class="pa-1"
                v-for="Product in Products"
                :key="Product.id"
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
                    style="
                      overflow: hidden;
                      background-color: transparent;
                      position: relative;
                    "
                    color=""
                    outlined
                  >
                    <div v-if="Product.discountPercent" class="best-price-tag">
                      <small class="discountPercent">
                        {{ Product.discountPercent }}-
                      </small>
                    </div>
                    <v-img
                      height="130"
                      :src="getimageUrl(Product.folder, Product.image)"
                    ></v-img>
                    <v-card-text
                      class="d-inline-block card-text py-1 pa-2 text-truncate"
                    >
                      {{ Product.name }} {{ Product.company }}
                    </v-card-text>
                    <v-card-actions class="py-0 justify-center">
                      <strong class="PriceAfter text-truncate">
                        {{ Product.payment }}
                        <small class="text-truncate">ريال</small>
                      </strong>
                    </v-card-actions>
                    <v-card-actions class="py-1 justify-space-between">
                      <p class="ma-0 sold-info text-truncate">
                        <span>{{ Product.id }} </span>بيعت
                      </p>
                      <span class="sold-info">
                        {{ Product.location }}
                      </span>
                    </v-card-actions>
                  </v-card>
                </div>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-sheet>
    </v-container>
    <FixedBottomNav class="hidden-sm-and-up" />
  </div>
</template>

<script>
import TheNavBar from "../NavBar/TheNavBar.vue";
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
import Products from "../data-json/All-Car.json";
import FilterSearch from "./FilterSearch.vue";
export default {
  name: "Products",
  components: { FixedBottomNav, TheNavBar, FilterSearch },
  data() {
    return {
      Products,
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      filterdialog: null,
      admins: [
        ["Management", "mdi-account-multiple-outline"],
        ["Settings", "mdi-cog-outline"],
      ],
      cruds: [
        ["Create", "mdi-plus-outline"],
        ["Read", "mdi-file-outline"],
        ["Update", "mdi-update"],
        ["Delete", "mdi-delete"],
      ],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Products {
  width: 100%;
  min-height: 70vh;
  background-color: $color-background;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
  .sold-info {
    font-family: $fontfamliy3 !important;
    font-size: 13px !important;
    font-weight: 600 !important;
    color: $fontcolorlinks !important;
    span {
      color: #000000 !important;
      margin-left: 5px;
      font-size: 14px !important;
      letter-spacing: 1.5px !important;
    }
  }
  // .seeMoreBtn {
  //   letter-spacing: 0 !important;
  //   font-size: 16px;
  //   font-family: $fontfamliy3;
  //   color: $color-2;
  // }
}
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
  letter-spacing: 0 !important;
  font-size: 15px !important;
  // font-weight: 600 !important;
}

// ::v-deep .overflow-y-auto.transparent.v-sheet.theme--light::-webkit-scrollbar {
//   display: none;
// }
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
.card-text {
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
  font-size: 13px !important;
}

.PriceAfter {
  font-size: 17px !important;
  color: $color-2;
  font-weight: 600 !important;
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
  z-index: 1;
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

//
.ribbon {
  position: absolute;
  top: 3px;
  right: 0px;
  z-index: 1;
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
@media (max-width: 1260px) {
  .container {
    max-width: 100% !important;
  }
}
@media (max-width: 600px) {
  .container {
    padding: 0;
  }
}
::v-deep .v-banner__wrapper {
  padding: 0 !important;
  border: 0 !important;
}
::v-deep .v-banner__content {
  padding: 0 !important;
  border: 0 !important;
  z-index: 50;
}
</style>
