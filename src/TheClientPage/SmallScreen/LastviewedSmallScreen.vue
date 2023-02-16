<template>
  <div class="last-seen">
    <v-app-bar class="mb-5" app flat>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="22">mdi-database-eye </v-icon>
        شوهدت مؤخرا
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="container pa-0 mt-14">
      <v-row no-gutters>
        <v-col cols="12" class="pa-2 pb-1">
          <v-card color="grey lighten-3" class="pa-2 mt-">
            <v-card-title class="toolbar-date pa-0 pb-1">
              التاريخ :</v-card-title
            >
            <v-menu
              ref="menu"
              v-model="menu"
              :close-on-content-click="false"
              :return-value.sync="dates"
              transition="scale-transition"
              offset-y
              min-width="auto"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-combobox
                  v-model="dates"
                  chips
                  readonly
                  clearable
                  dense
                  outlined
                  hide-details
                  deletable-chips
                  v-bind="attrs"
                  v-on="on"
                ></v-combobox>
              </template>
              <v-date-picker v-model="dates" no-title scrollable>
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="menu = false">
                  Cancel
                </v-btn>
                <v-btn text color="primary" @click="$refs.menu.save(dates)">
                  OK
                </v-btn>
              </v-date-picker>
            </v-menu>
          </v-card>
        </v-col>
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
                background-color: #fff;
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
                <!-- <strong
                    class="grey--text text--lighten-1 PriceBefore text-truncate"
                  >
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong> -->
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
    </v-container>
  </div>
</template>
<script>
import Products from "../../data-json/All-Car.json";
import "swiper/css/swiper.css";
export default {
  name: "BestOffer",
  components: {},
  data() {
    return {
      Products,
      menu: false,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
    };
  },
  // this is help full to call the image inside folder and inject to the src
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
.last-seen {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;

  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 15px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }
  .toolbar-date {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolor !important;
    font-size: 18px !important;
    font-weight: 600;
  }
  .card-text {
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
    letter-spacing: 0 !important;
    font-size: 14px !important;
  }
}
.sold-info {
  font-family: $fontfamliy3 !important;
  font-size: 13px !important;
  font-weight: 600 !important;
  color: $fontcolorlinks;
  span {
    color: #000000 !important;
    margin-left: 5px;
    font-size: 14px !important;
    letter-spacing: 1.5px !important;
  }
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
.seeMoreBtn {
  letter-spacing: 0 !important;
  font-size: 16px;
  font-family: $fontfamliy3;
  color: $color-2;
  background-color: #ffffff !important;
}
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
</style>
