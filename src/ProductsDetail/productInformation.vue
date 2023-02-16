<template>
  <!-- this component will be under the image  -->
  <div class="ContactSeller">
    <!-- here the product name  -->
    <v-col cols="12" class="pa-1">
      <p class="ProductName d-block text-truncate ma-0">
        {{ getCarInfo.company }} {{ getCarInfo.name }}
        {{ getCarInfo.modle }}
      </p>
    </v-col>
    <!-- <v-col cols="12" class="py-2">
      <ShareSaveReport />
    </v-col> -->
    <!-- here the Price Info   -->
    <v-row no-gutters align="center" justify="space-between" class="pa-1">
      <p class="ma-0 price">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <span class="mx-1 grey--text">-</span>
      <p class="ma-0 price">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <p class="ma-0 if-discount mr-2 grey--text text--lighten-1">
        {{ getCarInfo.payment }}
        <span> ريال </span>
      </p>
      <v-spacer></v-spacer>
      <v-chip class="discount-tag mx-1 justify-center">
        <span>9%</span>
        <span>خصم</span>
      </v-chip>
    </v-row>
    <!-- here are the rating and sales Info   -->
    <v-row align="center" no-gutters class="pa-1">
      <p class="ma-0">التقيمات</p>
      <span class="grey--text number text--darken-1 mr-1"> 9 </span>
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
      <span class="grey--text number text--darken-1 mr-1"> 33 </span>
      <v-spacer></v-spacer>
      <ShareSaveReport />
    </v-row>
    <!-- here are the vouchers -->
    <v-menu max-width="700" bottom left>
      <template v-slot:activator="{ on, attrs }">
        <v-card-actions class="pa-1 py-4" v-bind="attrs" v-on="on">
          <span class="see-more-coupons">القسائم</span>
          <v-sheet class="px-2 transparent d-flex" width="100%">
            <v-card color="#eee" flat v-for="i in 3" :key="i" class="coupons">
              خصم
              <span class="mx-1">20%</span>
              <ul class="Voucher-sm">
                <li></li>
                <li></li>
                <li></li>
              </ul>
            </v-card>
            <v-spacer></v-spacer>
            <span style="font-size: 13px" class="see-more-coupons"
              >رؤية الكل</span
            >
          </v-sheet>
        </v-card-actions>
      </template>
      <v-sheet
        style="overflow-y: scroll"
        height="300"
        class="pa-2 StoreVoucher"
        color="#ffffff"
      >
        <!-- <v-card-title class="titel py-2"> قسائم المتجر </v-card-title>
        <v-divider></v-divider> -->
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
              <!-- <div class="copy-button">
        <input id="copyvalue" type="text" readonly value="GOFREE" />
        <button onclick="copyIt()" class="copybtn">COPY</button>
      </div> -->
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
  font-weight: 500;
  letter-spacing: 0 !important;
  font-size: 23px !important;
  width: 100%;
  @media (max-width: 600px) {
    font-size: 17px !important;
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
  font-size: 14px;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
  @media (max-width: 400px) {
    font-size: 12px !important;
  }
}
.number {
  border-bottom: 1.5px solid rgba(128, 128, 128, 0.718);
  @media (max-width: 600px) {
    font-size: 14px !important;
  }
  @media (max-width: 400px) {
    font-size: 12px !important;
  }
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

  font-weight: 600;
  @media (max-width: 500px) {
    font-size: 13px;
  }
}
.discount-tag span:last-child {
  font-family: $fontfamliy3 !important;
  margin-right: 3px;
  color: #fff !important;
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
  margin: 0 3px;
  font-size: 12px;
  color: $fontcolorlinks !important;
  border-radius: 3px;
  font-weight: 600 !important;
  @media (max-width: 600px) {
    font-size: 12px;
  }
}
.see-more-coupons {
  font-family: $fontfamliy3 !important;
  color: $fontcolorlinks;
  font-size: 14px;
  @media (max-width: 600px) {
    font-size: 13px;
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
.Voucher-sm {
  position: absolute;
  top: 0;
  left: -2px;
  padding: 0;
  z-index: 5;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  li {
    list-style: none;
    width: 4px;
    height: 4px;
    background-color: #eee;
    border-radius: 50%;
  }
}
::v-deep
  span.discount-tag.mx-1.justify-center.v-chip.v-chip--no-color.theme--light.v-size--default {
  height: 30px;
}
</style>
