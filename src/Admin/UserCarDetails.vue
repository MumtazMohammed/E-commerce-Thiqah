<template>
  <div class="CarDetail">
    <v-container>
      <Services />
      <v-card class="pa-2 overflow-hidden">
        <v-img
          v-if="
            ActiveImage.length < 1
              ? (ActiveImage = getimageUrl(getCarInfo.folder, getCarInfo.image))
              : ActiveImage
          "
          :src="ActiveImage"
          :lazy-src="ActiveImage"
          class="ma-sm-auto"
          aspect-ratio="1.8"
          max-height="300"
          max-width="500"
          contain
        >
        </v-img>
        <v-sheet
          color="transparent"
          class="mx-auto"
          elevation="0"
          max-width="800"
        >
          <v-slide-group
            v-model="model"
            class="pa-0"
            center-active
            show-arrows
            mandatory
          >
            <v-slide-item
              v-for="(singleImage, x) in getCarInfo.images"
              :key="x"
              v-slot="{ active, toggle }"
            >
              <v-card
                flat
                class="ma-1 grey overflow-hidden"
                width="80"
                @click="toggle"
              >
                <v-row class="fill-height" align="center" justify="center">
                  <v-avatar tile size="80" color="transparent">
                    <v-img
                      :class="active ? '' : 'not-active-img'"
                      contain
                      @click="
                        ActiveImage = getimageUrl(
                          getCarInfo.folder,
                          singleImage
                        )
                      "
                      :src="getimageUrl(getCarInfo.folder, singleImage)"
                    />
                  </v-avatar>
                </v-row>
              </v-card>
            </v-slide-item>
          </v-slide-group>
        </v-sheet>
        <v-card-actions>
          <v-btn icon dark class="blue">
            <v-icon>mdi-home</v-icon>
          </v-btn>
          <v-card-title class="text">
            أسم المعلن :
            <p class="mb-0 mr-1">محمد أمين</p>
          </v-card-title>
          <!--  -->
          <v-spacer></v-spacer>
          <!-- pause  -->
          <v-dialog v-model="pause" persistent max-width="500">
            <template v-slot:activator="{ on, attrs }">
              <v-btn dark v-bind="attrs" v-on="on" class="orange darken-2">
                توقيف
              </v-btn>
            </template>
            <v-card>
              <v-textarea
                solo
                name="input-7-4"
                label="سبب التوقيف"
                :hide-details="true"
                flat
                no-resize
              ></v-textarea>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="green darken-2" text @click="pause = false">
                  تأكيد التوقيف
                </v-btn>
                <v-btn color="red darken-1" text @click="pause = false">
                  إلغاء
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
          <!-- delete  -->
          <v-btn dark class="red">حذف </v-btn>
        </v-card-actions>
        <!-- Car Report  -->
        <CarReport />
        <!--  -->
        <v-row justify="center mt-2">
          <v-col cols="12" class="pa-0">
            <v-card-title class="justify-center card-title">
              تفاصيل السيارة
            </v-card-title>
            <span class="line mb-3 mx-auto"></span>
          </v-col>
          <v-col cols="12" class="pa-1 position-relative detail-card-box">
            <v-card tile flat class="d-flex detail-card flex-wrap pa-5">
              <v-flex xs6 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-key</v-icon
                  >
                  مـاركة : <b class="pa-0">{{ getCarInfo.company }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-side</v-icon
                  >
                  الـنوع : <b class="pa-0">{{ getCarInfo.name }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-shape-outline</v-icon
                  >
                  الـفئة :
                  <b class="pa-0">{{ getCarInfo.type }}</b></v-card-text
                >
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-cogs</v-icon
                  >
                  الـسنة : <b class="pa-0">{{ getCarInfo.modle }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-arrow-left-bottom-bold</v-icon
                  >
                  الـوارد :
                  <b class="pa-0">{{ getCarInfo.received }}</b></v-card-text
                >
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-format-color-fill</v-icon
                  >
                  لـون الـمركبه : <b class="pa-0">{{ getCarInfo.ccolor }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-shift-pattern</v-icon
                  >
                  نـوع القير : <b class="pa-0">{{ getCarInfo.transmission }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-engine-outline</v-icon
                  >
                  حجم الـمحرك :
                  <b class="12a-0">{{ getCarInfo.engainpower }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-source-pull</v-icon
                  >
                  نـوع الـدفع : <b class="pa-0">{{ getCarInfo.boost }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-info</v-icon
                  >
                  حـالـة الـسيارة :
                  <b class="pa-0">{{ getCarInfo.condtion }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-gas-station</v-icon
                  >
                  نوع الوقود : <b class="pa-0">{{ getCarInfo.fuel }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-settings</v-icon
                  >
                  الـمواصفات : <b class="pa-0">{{ getCarInfo.kilometer }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-car-speed-limiter</v-icon
                  >
                  الـممشى : <b class="pa-0">{{ getCarInfo.kilometer }}</b>
                </v-card-text>
              </v-flex>
              <v-flex xs12 sm4 md3>
                <v-card-text class="table_data-child px-1 pl-0">
                  <v-icon class="grey--text text--lighten-2" right
                    >mdi-map-marker-radius</v-icon
                  >
                  المنطقة : <b class="pa-0">{{ getCarInfo.location }}</b>
                </v-card-text>
              </v-flex>
              <v-row justify="center" class="mt-2">
                <v-col cols="12" md="12" class="disc-p">
                  <v-card color="transparent" class="disc-title">
                    <!-- discrption  -->
                    <v-card-title class="disc-title">
                      تفاصيل أكثر عن السيارة....
                    </v-card-title>
                    <v-card-text class="disc-text pa-2">
                      هذا النص هو مثال لنص يمكن أن يستبدل في نفس المساحة، لقد تم
                      توليد هذا النص من مولد النص العربى، حيث يمكنك أن تولد مثل
                      هذا النص أو العديد من النصوص الأخرى إضافة إلى زيادة عدد
                      الحروف التى يولدها التطبيق. هذا النص هو مثال لنص يمكن أن
                      يستبدل في نفس المساحة، لقد تم توليد هذا النص من مولد النص
                      العربى، حيث يمكنك أن تولد مثل هذا النص أو العديد من النصوص
                      الأخرى إضافة إلى زيادة عدد الحروف التى يولدها التطبيق.
                    </v-card-text>
                    <!-- Note  -->
                    <v-card-title class="disc-title">
                      ملاحظات....
                    </v-card-title>
                    <v-list>
                      <v-card-actions class="flex-wrap">
                        <v-list-item
                          width="20"
                          v-for="(item, i) in items"
                          :key="i"
                        >
                          <span class="font-weight-bold">{{ i + 1 }}</span>
                          <span class="mx-2 font-weight-bold">-</span>
                          <v-list-item-content>
                            <v-list-item-title
                              v-text="item.text"
                            ></v-list-item-title>
                          </v-list-item-content>
                        </v-list-item>
                      </v-card-actions>
                    </v-list>
                  </v-card>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
          <!-- card discrption  -->
          <!--  -->
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import CarData from "../data-json/All-Car.json";
import Services from "../Admin/Services.vue";
import CarReport from "../Admin/CarReport.vue";
export default {
  name: "CarDetail",
  components: { Services, CarReport },
  data() {
    return {
      model: null,
      ActiveImage: "",
      width: 300,
      dialog: false,
      pause: false,
      GetCarData: CarData,
      carId: this.$route.params.carId,
      items: [
        { text: "يمكنك أن تولد مثل هذا النص" },
        { text: "يمكنك أن تولد مثل هذا النص" },
        { text: "يمكنك أن تولد مثل هذا النص" },
      ],
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
.CarDetail {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
  padding: $padding;
  font-family: $fontfamliy !important;
  letter-spacing: 0px !important;
}
.text {
  font-family: $fontfamliy !important;
  letter-spacing: 0px !important;
}
.not-active-img {
  position: relative;
}
.not-active-img::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: black;
  // z-index: 1;
  opacity: 0.5;
}
::v-deep .v-slide-group__next {
  min-width: 30px;
}
::v-deep .v-slide-group__prev {
  min-width: 30px;
}
::v-deep .v-slide-group__content {
  justify-content: center;
}
.detail-card {
  background: $color-2 !important;
}
.table_data-child {
  font-size: 16px !important;
  font-weight: bold;
  color: $fontcolorsm;
  letter-spacing: 0 !important;
  font-family: $fontfamliy;
}
.table_data-child b {
  font-size: 17px !important;
  font-weight: 400;
  color: $fontcolorsm;
  padding: 5px;
  font-family: $fontfamliy;
}

.card-title {
  font-size: 28px !important;
  font-weight: bold;
  color: $fontcolor;
  letter-spacing: 0 !important;
  font-family: $fontfamliy;
}
.disc-p {
  @media (max-width: 960px) {
    padding: 4px;
  }
}
.disc-title {
  color: $fontcolorsm;
  font-family: $fontfamliy;
}
.disc-text {
  font-family: $fontfamliy;
  font-size: 15px;
  font-weight: 500 !important;
  line-height: 1.9;
  background-color: #fff;
  color: $fontcolor !important;
  // border-radius: 3px !important;
}
.line {
  width: 30px;
  height: 5px;
  background-color: $color-2;
  display: block;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}
::v-deep .v-list-item {
  flex: 1 1 auto;
}
::v-deep .v-btn__content {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-weight: 500;
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  // font-weight: 500;
}
</style>
