<template>
  <div class="ShowRoomPageInfo">
    <v-container>
      <v-row>
        <v-col cols="12">
          <h2 class="header-title mb-3">صفحة صاحب المعرض</h2>
          <v-card-actions>
            <!-- send message -->
            <div class="mx-1">
              <v-dialog v-model="dialog" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    icon
                    elevation="2"
                    color="white"
                    class="success lighten-1"
                  >
                    <v-icon>mdi-chat-outline</v-icon>
                  </v-btn>
                </template>
                <v-card class="">
                  <v-card-actions>
                    <v-text-field
                      hide-details="true"
                      placeholder="عنوان الرسالة"
                    ></v-text-field>
                  </v-card-actions>
                  <v-card-actions>
                    <v-textarea
                      no-resize
                      rows="6"
                      class="pt-0 mt-0"
                      placeholder="الرسالة"
                      hide-details="true"
                    >
                    </v-textarea>
                  </v-card-actions>
                  <v-card-actions class="justify-center">
                    <v-btn class="send-btn">إرسال</v-btn>
                  </v-card-actions>
                  <v-divider></v-divider>
                  <v-card-actions>
                    <v-btn
                      class="send-btn"
                      color="primary"
                      outlined
                      @click="dialog = false"
                    >
                      إلغاء
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </div>
            <!-- Stop and play  -->
            <div class="mx-1">
              <v-dialog v-model="Rental" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    icon
                    elevation="2"
                    color="white"
                    class="blue lighten-2"
                  >
                    <v-icon v-if="!extand">mdi-stop-circle-outline</v-icon>
                    <v-icon v-if="extand">mdi-play-circle-outline</v-icon>
                  </v-btn>
                </template>
                <v-card class="">
                  <v-card-actions>
                    <v-text-field
                      type="number"
                      hide-details="true"
                      placeholder="المدة"
                      suffix="يوم"
                      outlined
                    ></v-text-field>
                  </v-card-actions>
                  <v-card-actions class="justify-center">
                    <v-btn
                      @click="(Rental = false), (extand = true)"
                      dark
                      elevation="0"
                      class="blue send-btn"
                    >
                      تمديد
                    </v-btn>
                  </v-card-actions>
                  <v-divider></v-divider>
                  <v-card-actions>
                    <v-btn
                      class="send-btn"
                      color="primary"
                      outlined
                      @click="Rental = false"
                    >
                      إلغاء
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </div>
            <!-- delete the account -->
            <div class="mx-1">
              <v-btn icon elevation="2" color="white" class="red lighten-2">
                <v-icon>mdi-trash-can-outline</v-icon>
              </v-btn>
            </div>
            <div class="mx-1">
              <v-btn
                @click="featured = true"
                icon
                elevation="2"
                color="white"
                class="indigo lighten-2"
              >
                <v-icon>mdi-arrow-up-bold-hexagon-outline</v-icon>
              </v-btn>
            </div>
          </v-card-actions>
          <v-card flat tile color="transparent">
            <v-card-actions class="justify-center">
              <div v-if="featured">
                <v-icon right class="green--text"> mdi-check </v-icon>
                <a class="grey--text">معرض متميز</a>
              </div>
            </v-card-actions>
          </v-card>
          <v-divider></v-divider>
          <v-card class="mt-3" tile flat color="transparent">
            <v-card-actions class="justify-center">
              <v-img
                contain
                max-width="200"
                src="../assets/pp.jpg"
                alt="../assets/pp.jpg"
                style="border-radius: 10px"
              />
            </v-card-actions>
            <ul class="Info-list">
              <li>
                <v-card-title class="text py-2"> أسم المعرض : </v-card-title>
              </li>

              <li>
                <v-card-title class="text py-2"> مالك المعرض : </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2"> المنطقة : </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2"> نوع المعرض : </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2"> عدد السيارات : </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2">
                  البريد الأكتروني :
                </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2"> رقم التعريف : </v-card-title>
              </li>
              <li>
                <v-card-title class="text py-2"> كلمة المرور : </v-card-title>
              </li>
            </ul>
          </v-card>
          <v-card-actions class="justify-space-between mt-2">
            <v-card width="550">
              <v-card-text class="text-center text">
                أرقام الأتصال
              </v-card-text>
              <ul class="contact-list">
                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>
                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>
                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>
              </ul>
            </v-card>
            <v-card width="550">
              <v-card-text class="text-center text">
                أرقام الوتس آب
              </v-card-text>
              <ul class="contact-list">
                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>

                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>
                <li>
                  <v-card-title class="text py-2"> 01121331731 </v-card-title>
                </li>
              </ul>
            </v-card>
          </v-card-actions>
        </v-col>
        <!-- Cars Cards  -->
        <v-col cols="12" class="">
          <v-card outlined class="pa-3">
            <h3 class="header-title">سيارات المعرض</h3>
          </v-card>
        </v-col>
        <!-- guide colors  -->
        <v-col cols="12" class="py-0">
          <div class="d-flex">
            <div class="d-flex align-center ma-2">
              <span class="dot-trusted"></span>
              <v-card-subtitle class="pa-0 pr-2"> موثق </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-Nottrusted"></span>
              <v-card-subtitle class="pa-0 pr-2"> غير موثق </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-upgrade"></span>
              <v-card-subtitle class="pa-0 pr-2"> مترقي </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-feature"></span>
              <v-card-subtitle class="pa-0 pr-2"> معزز </v-card-subtitle>
            </div>
          </div>
        </v-col>
        <!-- search for Cars -->
        <v-col cols="12" class="pa-0">
          <v-card-actions class="justify-center">
            <v-card
              flat
              outlined
              class="search-card d-flex align-center overflow-hidden"
              width="500"
            >
              <!-- delete text  -->
              <v-btn
                v-if="search.length > 0"
                small
                icon
                color="white"
                class="mr-1 red darken-1"
                @click="reset()"
              >
                <v-icon class="">mdi-close</v-icon>
              </v-btn>
              <!-- customiza search -->
              <v-text-field
                class="rounded-b-0"
                v-model="search"
                solo
                large
                flat
                label="بحث عن سيارة ؟"
                hide-details="true"
                background-color="#fff"
                append-icon="mdi-store-search-outline"
              ></v-text-field>
            </v-card>
          </v-card-actions>
        </v-col>
        <!--  -->
        <v-col cols="12" md="4" sm="6" v-for="(Car, i) in Cars" :key="i">
          <v-sheet color="transparent">
            <v-card-actions class="py-0 justify-space-between">
              <v-card-subtitle class="pa-0"> محجوز </v-card-subtitle>
              <div class="d-flex">
                <span v-if="Car.Trusted" class="dot-trusted ma-1"></span>
                <span v-else class="dot-Nottrusted ma-1"></span>
                <span v-if="Car.Vip" class="dot-upgrade ma-1"></span>
                <span class="dot-feature ma-1"></span>
              </div>
            </v-card-actions>
          </v-sheet>
          <v-card
            :to="{
              name: 'UserCarDetails',
              params: {
                carId: Car.id,
              },
            }"
            outlined
            class="overflow-hidden"
          >
            <v-row>
              <v-col cols="3">
                <v-avatar tile size="70" color="grey darken-4">
                  <v-img
                    contain
                    :src="getimageUrl(Car.folder, Car.image)"
                    :lazy-src="getimageUrl(Car.folder, Car.image)"
                    :alt="getimageUrl(Car.folder, Car.image)"
                  />
                </v-avatar>
              </v-col>
              <v-col cols="9">
                <v-card-text class="text text-center py-1"
                  >{{ Car.id }}
                </v-card-text>
                <v-card-text class="text text-center py-1">
                  23 / 05 / 2022
                </v-card-text>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import Cars from "@/data-json/All-Car.json";
export default {
  name: "UserPAgeInfo",
  data() {
    return {
      search: "",
      ShowSerachCard: "",
      Cars,
      carId: this.$route.params.CarType,
      dialog: false,
      Rental: false,
      extand: false,
      featured: false,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
    reset() {
      return (this.search = "");
    },
  },
  computed: {
    filteredStore: function () {
      return this.Cars.filter((showroom) => {
        return showroom.id.match(this.search);
      });
    },
    length() {
      return 7000;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ShowRoomPageInfo {
  width: 100%;
  min-height: 100vh;
  padding: $padding;
  background-color: $color-background;
  font-family: $fontfamliy !important;

  .text {
    font-family: $fontfamliy;
    letter-spacing: 0px;
    font-size: 17px !important;
  }
  .header-title {
    font-family: $fontfamliy;
    letter-spacing: 0px;
    text-align: center;
  }
  .dot-trusted {
    width: 7px;
    font-family: $fontfamliy;

    height: 7px;
    display: block;
    background-color: #43a047;
    border-radius: 50%;
  }
  .dot-Nottrusted {
    width: 7px;
    font-family: $fontfamliy;
    height: 7px;
    display: block;
    background-color: #d23819;
    border-radius: 50%;
  }
  .dot-upgrade {
    width: 7px;
    font-family: $fontfamliy;

    height: 7px;
    display: block;
    background-color: #40c4ff;
    border-radius: 50%;
  }
  .dot-feature {
    width: 7px;
    font-family: $fontfamliy;

    height: 7px;
    display: block;
    background-color: #f57c00;
    border-radius: 50%;
  }
}
::v-deep.theme--light.v-input input::placeholder {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
::v-deep.theme--light.v-input textarea::placeholder {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
.send-btn {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-weight: bold;
}
.Info-list {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  // justify-content: center;
  padding: 0;
  li {
    flex-basis: 31%;
    border: 1px solid rgba(128, 128, 128, 0.17) !important;
    margin: 1.5px;
    @media (max-width: 800px) {
      flex-basis: 49%;
    }
    @media (max-width: 500px) {
      flex-basis: 100%;
    }
  }
}
.contact-list {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  padding: 0;
  li {
    flex-basis: 50%;
    border: 0.5px solid rgba(128, 128, 128, 0.081) !important;
    @media (max-width: 500px) {
      flex-basis: 100%;
    }
  }
}
</style>
