<template>
  <div class="Product-Ratings mb-2">
    <!-- Product Ratings  -->
    <v-sheet color="orange lighten-5" class="overflow--hidden">
      <v-card-text class="pa-3 tital">تـقـييـات الـمـنـتج</v-card-text>
      <v-col cols="12" class="py-0">
        <strong class="pb-1">
          <span>{{ rating }}</span>
          من 5
        </strong>
        <v-rating
          v-model="rating"
          half-increments
          small
          background-color="orange"
          color="orange"
          readonly
        ></v-rating>
      </v-col>
      <v-col cols="12" class="pa-0">
        <v-chip-group
          class="filter-rating"
          mandatory
          center-active
          active-class="white--text orange"
        >
          <v-chip small> <span class="ml-2">(40)</span> الكل </v-chip>
          <v-chip small> <span class="ml-2">(20)</span> 1 نجوم </v-chip>
          <v-chip small> <span class="ml-2">(20)</span> 2 نجوم </v-chip>
          <v-chip small> <span class="ml-2">(20)</span> 3 نجوم </v-chip>
          <v-chip small> <span class="ml-2">(20)</span> 4 نجوم </v-chip>
          <v-chip small> <span class="ml-2">(20)</span> 5 نجوم </v-chip>
        </v-chip-group>
      </v-col>
      <!-- If no rating  -->
      <v-col cols="12">
        <v-card-text class="text-center no-rating">
          لا يوجد أي تقيمات
        </v-card-text>
      </v-col>
      <!--  rating  -->
      <v-col cols="12" class="pa-2">
        <v-card color="#fff" tile outlined height="auto" class="comment">
          <v-card-actions class="pa-0">
            <div class="">
              <v-card-text class="pa-0 Customer-name"> محمد أمين </v-card-text>
              <v-rating
                v-model="rating"
                half-increments
                small
                background-color="orange darken-1"
                color="orange darken-1"
                readonly
              ></v-rating>
            </div>
            <v-spacer></v-spacer>
            <v-card-text class="pa-0 grey--text Customer-name">
              14/07/2024
            </v-card-text>
          </v-card-actions>
          <v-sheet color="transparent" class="my-1">
            <v-card-subtitle class="pa-1 Customer-comment">
              الشكل والمبنى، من المهم أن يكون الموقع جاذبا من الناحية البصرية
              فهو يساعد المتصفح على فهم المحتوى أكثر وبالإضافة إلى الألوان التي
              ستجعل موقعك ذا إحساس عالي. التنوين، وهو على ثلاث أشكال: تنوين ضم
              وتنوين فتح وتنوين كسر هذا نص عشوائي الشكل والمبنى، من المهم أن
              يكون الموقع جاذبا من الناحية البصرية فهو يساعد المتصفح على فهم
              المحتوى أكثر وبالإضافة إلى الألوان التي ستجعل موقعك ذا إحساس عالي.
              التنوين، وهو على ثلاث أشكال: تنوين
            </v-card-subtitle>
          </v-sheet>
          <!-- big screen customer img  -->
          <div class="hidden-xs-only">
            <v-sheet class="mt-1" color="grey lighten-2 ">
              <v-avatar
                v-for="(singleImage, x) in getCarInfo.images"
                :key="x"
                class="ma-1"
                rounded
                size="50"
                color="grey darken-2"
                @click="
                  ActiveImage = getimageUrl(getCarInfo.folder, singleImage)
                "
              >
                <v-img :src="getimageUrl(getCarInfo.folder, singleImage)">
                </v-img>
              </v-avatar>
            </v-sheet>
            <v-btn
              class="close-comment-img"
              color="grey lighten-2"
              elevation="0"
              tile
              v-if="ActiveImage.length > 0"
              @click="ActiveImage = ''"
            >
              إغلاق
            </v-btn>
            <v-card-actions
              v-if="ActiveImage.length > 0"
              class="justify-center pa-0"
            >
              <v-avatar tile height="300" width="500">
                <v-img
                  contain
                  :src="ActiveImage"
                  :lazy-src="ActiveImage"
                ></v-img>
              </v-avatar>
            </v-card-actions>
          </div>
          <!-- small screen customer img  -->
          <div class="hidden-sm-and-up">
            <v-dialog
              v-model="dialog"
              fullscreen
              hide-overlay
              transition="dialog-bottom-transition"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-sheet class="mt-1" color="grey lighten-2 ">
                  <v-avatar
                    v-bind="attrs"
                    v-on="on"
                    v-for="(singleImage, x) in getCarInfo.images"
                    :key="x"
                    class="ma-1"
                    rounded
                    size="40"
                    color="grey darken-2"
                  >
                    <v-img :src="getimageUrl(getCarInfo.folder, singleImage)">
                    </v-img>
                  </v-avatar>
                  <v-avatar rounded class="ma-1" size="40" color="black">
                    <span class="white--text">
                      + {{ getCarInfo.images.length - 1 }}
                    </span>
                  </v-avatar>
                </v-sheet>
              </template>
              <v-card color="grey darken-4">
                <v-toolbar tile dark flat color="grey darken-3">
                  <v-btn icon dark @click="dialog = false">
                    <v-icon>mdi-close</v-icon>
                  </v-btn>
                  <v-spacer></v-spacer>
                  <v-toolbar-title>
                    {{ customerIMageNo + 1 }} /
                    {{ getCarInfo.images.length }}
                  </v-toolbar-title>
                </v-toolbar>
                <v-carousel
                  v-model="customerIMageNo"
                  height="620px"
                  width="100%"
                  touch
                  hide-delimiters
                >
                  <v-carousel-item
                    v-for="(singleImage, x) in getCarInfo.images"
                    :key="x"
                  >
                    <v-img :src="getimageUrl(getCarInfo.folder, singleImage)">
                    </v-img>
                  </v-carousel-item>
                </v-carousel>
              </v-card>
            </v-dialog>
          </div>
        </v-card>
      </v-col>
      <v-col cols="12" class="pa-1">
        <v-card-actions class="justify-center pa-0">
          <v-btn dark small class="elevation-0 show-all-btn orange"
            >مشاهدة الكل</v-btn
          >
        </v-card-actions>
      </v-col>
    </v-sheet>
  </div>
</template>
<script>
import CarData from "../data-json/All-Car.json";
export default {
  name: "ProductRatings",
  components: {},
  data() {
    return {
      rating: 3.6,
      ActiveImage: "",
      customerIMageNo: 0,
      dialog: false,
      GetCarData: CarData,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      items: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
        },
      ],
    };
  },
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
.tital {
  // text-align: center;
  font-family: $fontfamliy3;
  font-size: 22px;
  letter-spacing: 0 !important;
  color: $fontcolor !important;
  font-weight: 600;
  pointer-events: none;
  @media (max-width: 400px) {
    font-size: 18px;
  }
}
.detail-card {
  overflow: hidden;
  // box-shadow: 0 0 0 0.5px rgba(128, 128, 128, 0.519) !important;
}
.Customer-name {
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  width: fit-content;
  pointer-events: none;
}
.Customer-comment {
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  width: fit-content;
  font-size: 13px;
  pointer-events: none;
}
.close-comment-img {
  font-family: $fontfamliy2 !important;
  letter-spacing: 0 !important;
  color: red !important;
}
strong {
  color: #ff5722 !important;
  font-family: $fontfamliy3;
  font-size: 20px;
  margin-bottom: 5px;
  @media (max-width: 600px) {
    font-size: 18px;
  }
}
.filter-rating {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
.no-rating {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 20px;
  color: $fontcolorlinks;
  pointer-events: none;
  @media (max-width: 600px) {
    font-size: 17px;
  }
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
.comment:not(:first-child) {
  margin-top: 5px;
}
::v-deep .v-slide-group__next {
  align-items: center;
  display: flex;
  flex: 0 1 25px;
  justify-content: center;
  min-width: 25px;
}
::v-deep .v-slide-group__prev {
  align-items: center;
  display: flex;
  flex: 0 1 25px;
  justify-content: center;
  min-width: 25px;
}
::v-deep .v-image.v-responsive.theme--light {
  align-items: center;
}
.show-all-btn {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
</style>
