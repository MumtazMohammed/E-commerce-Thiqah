<template>
  <!-- this component will be under the image  -->
  <div class="ContactSeller">
    <!-- here the product name  -->
    <v-row no-gutters>
      <v-col class="pa-2 py-1">
        <p class="ProductName ma-0">
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
          {{ getCarInfo.company }} {{ getCarInfo.name }}
          {{ getCarInfo.modle }}
        </p>
      </v-col>
      <span small class="discount-tag ml-1 px-1">
        <span>25%</span>
      </span>
    </v-row>
    <!-- here the Price Info   -->
    <v-row no-gutters align="center" class="pa-2">
      <p class="ma-0 price">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <span class="mx-1 grey--text">-</span>
      <p class="ma-0 price">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <v-spacer></v-spacer>
      <p class="ma-0 if-discount mr-2 grey--text text--lighten-1">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
    </v-row>
    <!-- here the Guarantee    -->
    <v-row no-gutters align="center" class="">
      <v-sheet width="100%" color="red lighten-5">
        <!-- product Guarantee  -->
        <v-list-item two-line class="px-1 py-0">
          <v-icon color="red darken-2" size="27">mdi-shield-check</v-icon>
          <v-list-item-content class="pa-0 pr-2">
            <v-list-item-title class="Guarantee-text">
              100٪ أصلي
            </v-list-item-title>
            <v-list-item-subtitle class="Guarantee-text-tow">
              ضمان حقيقي أو استرد أموالك
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <!-- product Guarantee  -->
        <v-list-item two-line class="px-1 py-0">
          <v-icon color="red darken-2" size="27">
            mdi-chevron-triple-down
          </v-icon>
          <v-list-item-content class="pa-0 pr-2">
            <v-list-item-title class="Guarantee-text">
              أقل سعر مضمون
              <v-icon
                left
                style="transform: scaleX(-1)"
                size="19"
              >
                mdi-help-circle-outline
              </v-icon>
            </v-list-item-title>
            <v-list-item-subtitle class="Guarantee-text-tow">
              أوجد خيار أرخص؟ ستحصل عملات معدنية مجانية!
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-sheet>
    </v-row>
    <!-- here are the rating and sales Info   -->
    <v-row align="center" no-gutters class="pa-2">
      <p class="ma-0">التقيمات</p>
      <span class="number mr-1"> 9 </span>
      <v-divider vertical class="mx-2"></v-divider>
      <v-rating
        v-model="rating"
        half-increments
        background-color="orange"
        color="orange"
        small
        readonly
      ></v-rating>
      <!-- <span class="grey--text number text--darken-1 mr-1">
        {{ rating }}
      </span> -->
      <v-divider vertical class="mx-2"></v-divider>
      <p class="ma-0">المبيعات</p>
      <span class="number mr-1"> 33 </span>
      <v-spacer></v-spacer>
      <ShareSaveReport />
    </v-row>
    <!-- here are the Promotions -->
    <v-sheet color="#eee" class="py-md-1 py-lg-1 pt-2">
      <v-menu max-width="700" open-on-hover bottom left>
        <template v-slot:activator="{ on, attrs }">
          <v-card
            style="width: fit-content"
            class="promotion-card"
            flat
            tile
            min-width="100%"
            rounded=""
            v-bind="attrs"
            v-on="on"
          >
            <v-row no-gutters class="fill-height" align="center">
              <span class="text-for-all mx-2">العروض :</span>
              <v-col class="pa-1" v-for="i in 5" :key="i">
                <v-sheet dark class="text-center" color="orange">
                  <v-card-text class="pa-0 coupons">
                    خصم
                    <span class="mx-">20%</span>
                  </v-card-text>
                </v-sheet>
              </v-col>
            </v-row>
          </v-card>
        </template>
        <v-sheet
          style="overflow-y: scroll"
          height="300"
          class="pa-2 StoreVoucher"
          color="#ffffff"
        >
          <v-row no-gutters>
            <v-col
              class="pa-2"
              md="6"
              lg="6"
              sm="6"
              cols="12"
              v-for="n in 3"
              :key="n"
            >
              <v-card flat class="card" color="#eee">
                <v-row no-gutters justify="center" class="main">
                  <v-col style="border-left: 1px dashed grey" class="" cols="3">
                    <v-row
                      align="center"
                      style="height: 100%"
                      justify="center"
                      no-gutters
                    >
                      <v-avatar class="profile my-auto" color="grey" size="50">
                        <v-img
                          src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                        ></v-img>
                      </v-avatar>
                    </v-row>
                  </v-col>

                  <v-col class="pr-1" cols="6">
                    <v-card-subtitle class="text pa-1">
                      خصم <span class="mx-1 red--text"><span>20</span>%</span>
                    </v-card-subtitle>
                    <v-card-text class="pa-1 text">
                      أنفق
                      <span class="mx-1">
                        52<v-icon left size="17">mdi-currency-rial</v-icon>
                      </span>
                      كحد أدنى
                    </v-card-text>
                    <v-card-text class="pa-1 text">
                      متاح حتى
                      <span>10/2/2020</span>
                    </v-card-text>
                  </v-col>
                  <v-col cols="3">
                    <v-row
                      align="center"
                      style="height: 100%"
                      justify="center"
                      no-gutters
                    >
                      <v-btn small fab dark class="white btn" elevation="0">
                        أخذ
                      </v-btn>
                    </v-row>
                  </v-col>
                </v-row>
                <ul class="Voucher">
                  <li></li>
                  <li></li>
                  <li></li>
                  <li></li>
                  <li></li>
                  <li></li>
                </ul>
              </v-card>
            </v-col>
          </v-row>
        </v-sheet>
      </v-menu>
    </v-sheet>
  </div>
</template>
<script>
import CarData from "../data-json/All-Car.json";
import ShareSaveReport from "./ShareSaveReport.vue";
export default {
  name: "productInformation",
  components: { ShareSaveReport },
  data() {
    return {
      rating: 4.5,
      GetCarData: CarData,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      ShowPriceOption: true,
      ShowContac: false,
    };
  },
  // this is help full to call the image inside folder and inject to the src
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // this computed to call the item by it info
  computed: {
    getCarInfo() {
      let Carinformation = "";
      for (let i = 0; i < this.GetCarData.length; i++) {
        if (this.GetCarData[i].id == this.carId) {
          Carinformation = this.GetCarData[i];
          break;
        }
      }
      return Carinformation;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ProductName {
  font-family: $fontfamliy3 !important;
  color: $fontcolor !important;
  font-weight: 400;
  letter-spacing: 0 !important;
  font-size: 23px !important;
  display: -webkit-box !important;
  -webkit-line-clamp: 2 !important;
  -webkit-box-orient: vertical !important;
  overflow: hidden;
  pointer-events: none;
  @media (max-width: 960px) {
    font-size: 18px !important;
  }
  @media (max-width: 600px) {
    font-size: 16px !important;
  }
}
.price {
  font-size: 25px;
  font-weight: 600 !important;
  color: $color-2;
  font-family: sans-serif !important;
  font-weight: 700 !important;
  @media (max-width: 600px) {
    font-size: 18px !important;
  }
  @media (max-width: 350px) {
    font-size: 15px !important;
  }
}
.if-discount {
  font-size: 19px;
  text-decoration: line-through;
  font-weight: 700 !important;
  font-family: sans-serif !important;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
}
p {
  font-family: $fontfamliy3 !important;
  font-weight: 500;
  font-size: 16px;
  @media (max-width: 450px) {
    font-size: 14px !important;
  }
}
.number {
  font-family: sans-serif !important;
  border-bottom: 1.5px solid rgba(0, 0, 0, 0.718);
  font-size: 15px !important;
  color: $color-2;
  font-weight: 600;
}
::v-deep
  button.v-icon.notranslate.v-icon--link.material-icons.theme--light.orange--text {
  font-size: 15px !important;
  padding: 0.5px !important;
}
.discount-tag {
  background-color: $color-2 !important;
  color: #fff !important;
  font-size: 15px !important;
  clip-path: polygon(0 0, 100% 0%, 100% 100%, 50% 83%, 0 100%);
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 600;
  @media (max-width: 500px) {
    font-size: 13px;
  }
}

::v-deep ::v-deep .theme--light.v-btn:before {
  background-color: rgba(255, 255, 255, 0);
  transition: all 0.3s 0s ease;
}

::v-deep .theme--light.v-btn:hover:before {
  opacity: 0;
}
// coupons
.coupons {
  font-family: $fontfamliy3 !important;
  padding: 0px 5px;
  font-size: 12px;
  color: $fontcolorsm !important;
  font-weight: 600 !important;
  @media (max-width: 600px) {
    font-size: 12px;
  }
  @media (max-width: 350px) {
    font-size: 10px !important;
  }
  span {
    font-family: sans-serif !important;
  }
}
// Voucher
.StoreVoucher {
  background-color: $color-background;
  .titel {
    letter-spacing: 0 !important;
    font-size: 17px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 13px !important;
    font-weight: 600 !important;
  }
  .btn {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 14px !important;
    margin: 0 auto !important;
    font-weight: 600;
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
}
::v-deep.v-menu__content.theme--light.menuable__content__active {
  @media (max-width: 600px) {
    left: 7px !important;
    right: 7px !important;
  }
}
.Voucher {
  position: absolute;
  top: 0;
  left: -3px;
  padding: 5px 0;
  z-index: 5;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  li {
    list-style: none;
    width: 8px;
    height: 8px;
    background-color: #ffffff;
    border-radius: 50%;
    // border-right: 1px solid #42a5f5;
  }
}

::v-deep
  span.discount-tag.mx-1.justify-center.v-chip.v-chip--no-color.theme--light.v-size--default {
  height: 30px;
}
.text-for-all {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolor !important;
  // margin: 0 auto !important;
  font-weight: 500;
  @media (max-width: 450px) {
    font-size: 14px !important;
  }
}
.promotion-card {
  position: relative;
}
::v-deep .px-1.py-0.v-list-item.v-list-item--two-line.theme--light {
  min-height: 50px !important;
}
.Guarantee-text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
}
.Guarantee-text-tow {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  line-height: 1.5;
}
</style>
