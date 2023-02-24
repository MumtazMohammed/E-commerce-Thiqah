<template>
  <div class="Products">
    <TheNavBar />
    <v-container class="pa-0">
      <!-- small screen  -->
      <v-sheet
        style="height: calc(100vh - 106px); overflow-y: auto"
        class="hidden-md-and-up"
        color="#eee"
      >
        <v-banner style="z-index: 8" class="pa-0" sticky>
          <FilterSearch />
        </v-banner>
        <v-row no-gutters>
          <v-col
            cols="6"
            md="3"
            sm="4"
            lg="2"
            class="pa-1"
            v-for="Product in Products"
            :key="Product.id"
          >
            <v-hover v-slot="{ hover }">
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
                  :elevation="hover ? 3 : 0"
                  min-height="250px"
                  width="100%"
                  style="
                    overflow: hidden;
                    background-color: #fff;
                    position: relative;
                  "
                  rounded="lg"
                >
                  <div v-if="Product.discountPercent" class="best-price-tag">
                    <small class="discountPercent">
                      {{ Product.discountPercent }}-
                    </small>
                  </div>
                  <v-img
                    height="150"
                    :src="getimageUrl(Product.folder, Product.image)"
                  ></v-img>
                  <!--  product name  -->
                  <v-card-text
                    style="
                      display: -webkit-box;
                      -webkit-line-clamp: 2;
                      -webkit-box-orient: vertical;
                      overflow: hidden;
                    "
                    class="card-text py-1 pa-2"
                  >
                    <!-- if this product at thiqah mall  -->
                    <span
                      style="
                        background-color: #ff3d00;
                        border-radius: 3px;
                        font-weight: 600;
                        font-size: 12px;
                        padding: 1px;
                      "
                      class="white--text ml-1"
                    >
                      ثـقـة مـول
                    </span>

                    {{ Product.name }} {{ Product.company }} {{ Product.name }}
                    {{ Product.company }} {{ Product.name }}
                  </v-card-text>
                  <strong class="PriceAfter py-1 pt-0 pa-2 text-truncate">
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                  <!-- if the product contain any promotion -->
                  <v-card-text class="py-1 pa-2 text-truncate">
                    <!-- free delivery  -->
                    <span class="span-text">
                      <!-- <v-icon>mdi-moped</v-icon> -->
                      توصيل مجاناً
                    </span>
                    <!-- divider -->
                    <span class="divider mx-1"></span>
                    <!-- Discount coupon  -->
                    <span class="span-text"> قسيمة <span>50%</span> </span>
                    <!-- divider -->
                    <span class="divider mx-1"></span>
                    <!-- free coins  -->
                    <span class="span-text"> <span>20</span> نقطه </span>
                  </v-card-text>
                  <!-- how many sold and rating  -->
                  <v-card-actions class="py-0 pa-2">
                    <!-- rating  -->
                    <v-icon size="17" color="amber">mdi-star</v-icon>
                    <span class="span">3.5</span>
                    <!-- divider -->
                    <span class="divider mx-1"></span>
                    <!-- sold Info  -->
                    <p class="ma-0 sold-info text-truncate">
                      <span class="span ml-1">({{ Product.id }})</span>بيعت
                    </p>
                  </v-card-actions>
                  <!-- location -->
                  <v-card-actions class="pt-0 pb justify-end">
                    <span class="sold-info">
                      {{ Product.location }}
                    </span>
                  </v-card-actions>
                </v-card>
              </div>
            </v-hover>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- big screen  -->
      <v-sheet
        v-scroll.self="onScroll"
        class="pa-2 hidden-sm-and-down"
        color="#eee"
      >
        <v-row no-gutters>
          <v-col cols="2">
            <v-banner class="pa-0" sticky>
              <FilterSearch />
            </v-banner>
          </v-col>
          <v-col cols="10">
            <v-row no-gutters>
              <v-col
                cols="6"
                md="3"
                sm="4"
                lg="2"
                class="pa-1"
                v-for="Product in Products"
                :key="Product.id"
              >
                <v-hover v-slot="{ hover }">
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
                      :elevation="hover ? 3 : 0"
                      min-height="250px"
                      width="100%"
                      style="
                        overflow: hidden;
                        background-color: #fff;
                        position: relative;
                      "
                      rounded="lg"
                    >
                      <div
                        v-if="Product.discountPercent"
                        class="best-price-tag"
                      >
                        <small class="discountPercent">
                          {{ Product.discountPercent }}-
                        </small>
                      </div>
                      <v-img
                        height="150"
                        :src="getimageUrl(Product.folder, Product.image)"
                      ></v-img>
                      <!--  product name  -->
                      <v-card-text
                        style="
                          display: -webkit-box;
                          -webkit-line-clamp: 2;
                          -webkit-box-orient: vertical;
                          overflow: hidden;
                        "
                        class="card-text py-1 pa-2"
                      >
                        <!-- if this product at thiqah mall  -->
                        <span
                          style="
                            background-color: #ff3d00;
                            border-radius: 3px;
                            font-weight: 600;
                            font-size: 12px;
                            padding: 1px;
                          "
                          class="white--text ml-1"
                        >
                          ثـقـة مـول
                        </span>

                        {{ Product.name }} {{ Product.company }}
                        {{ Product.name }} {{ Product.company }}
                        {{ Product.name }}
                      </v-card-text>
                      <strong class="PriceAfter py-1 pt-0 pa-2 text-truncate">
                        {{ Product.payment }}
                        <small class="text-truncate">ريال</small>
                      </strong>
                      <!-- if the product contain any promotion -->
                      <v-card-text class="py-1 pa-2 text-truncate">
                        <!-- free delivery  -->
                        <span class="span-text">
                          <!-- <v-icon>mdi-moped</v-icon> -->
                          توصيل مجاناً
                        </span>
                        <!-- divider -->
                        <span class="divider mx-1"></span>
                        <!-- Discount coupon  -->
                        <span class="span-text"> قسيمة <span>50%</span> </span>
                        <!-- divider -->
                        <span class="divider mx-1"></span>
                        <!-- free coins  -->
                        <span class="span-text"> <span>20</span> نقطه </span>
                      </v-card-text>
                      <!-- how many sold and rating  -->
                      <v-card-actions class="py-0 pa-2">
                        <!-- rating  -->
                        <v-icon size="17" color="amber">mdi-star</v-icon>
                        <span class="span">3.5</span>
                        <!-- divider -->
                        <span class="divider mx-1"></span>
                        <!-- sold Info  -->
                        <p class="ma-0 sold-info text-truncate">
                          <span class="span ml-1">({{ Product.id }})</span>بيعت
                        </p>
                      </v-card-actions>
                      <!-- location -->
                      <v-card-actions class="pt-0 pb justify-end">
                        <span class="sold-info">
                          {{ Product.location }}
                        </span>
                      </v-card-actions>
                    </v-card>
                  </div>
                </v-hover>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-sheet>
    </v-container>
    <FixedBottomNav class="hidden-md-and-up" />
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
      rating: 3.6,
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
  padding-bottom: 10px;
  @media (max-width: 600px) {
    margin-bottom: 50px;
    padding-bottom: 0px;
  }
  .sold-info {
    font-family: $fontfamliy3 !important;
    font-size: 13px !important;
    font-weight: 500 !important;
    color: $fontcolor !important;
  }
  .span {
    font-family: sans-serif !important;
    margin-left: 5px;
    font-size: 13px !important;
    letter-spacing: 1.5px !important;
  }
  .span-text {
    font-family: $fontfamliy3 !important;
    font-size: 12px !important;
    border-radius: 2px;
    // padding: 2px;
    @media (max-width: 600px) {
      padding: 0px;
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
  font-size: 13.5px !important;
  // font-weight: 600 !important;
}
.PriceAfter {
  font-size: 17px !important;
  color: $color-2;
  font-weight: 600 !important;
  font-family: sans-serif !important;
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
::v-deep
  button.v-icon.notranslate.v-icon--link.material-icons.theme--light.orange--text {
  font-size: 23px !important;
  padding: 1px !important;
}
::v-deep
  button.v-icon.notranslate.v-icon--link.material-icons.theme--light.orange--text {
  font-size: 23px !important;
  padding: 1px !important;
  @media (max-width: 600px) {
    font-size: 17px !important;
  }
}
::v-deep
  button.v-icon.notranslate.v-icon--link.material-icons.theme--light.orange--text.text--darken-1 {
  font-size: 15px !important;
  padding: 1px !important;
}
.divider {
  display: inline-block;
  height: 12px;
  // width: 2px;
  padding: 1px;
  background-color: #e0e0e0;
  border-radius: 2px;
}
</style>
