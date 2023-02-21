<template>
  <div class="TheShowRoomPage">
    <!-- small Screen Tabs  -->
    <div class="hidden-md-and-up">
      <v-app-bar flat fixed color="#fc624d" dark>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-home </v-icon>
        </v-btn>
        <v-toolbar-title class="pr-1 titel">الرئيسية</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-arrow-left </v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet height="56"></v-sheet>
    </div>
    <v-container class="pa-0">
      <v-sheet class="py-md-3 py-lg-3">
        <!-- search  -->
        <v-col class="mx-auto" cols="12" md="7" lg="7">
          <v-card color="" outlined class="search overflow-hidden">
            <v-text-field
              class="rounded-sm elevation-0"
              v-model="search"
              solo
              flat
              dense
              clearable
              label="  أبحث عن أسم المنتج ؟ "
              hide-details="true"
              background-color="#fff"
              append-icon="mdi-store-search-outline"
              @focus="ShowSerachCardvisble = true"
            ></v-text-field>
          </v-card>
        </v-col>
        <!-- tabs  -->
        <v-tabs
          :show-arrows="false"
          v-model="tab"
          background-color="transparent"
          color="basil"
          center-active
        >
          <v-tab>
            الكل
            <v-spacer></v-spacer>
            <span>0</span>
          </v-tab>
          <v-tab>
            المتاح
            <v-spacer></v-spacer>
            <span>0</span>
          </v-tab>
          <v-tab>
            المباع
            <v-spacer></v-spacer>
            <span>0</span>
          </v-tab>
          <v-tab>
            متوقف
            <v-spacer></v-spacer>
            <span class="mr-2">0</span>
          </v-tab>
          <v-tab>
            مخالف
            <v-spacer></v-spacer>
            <span>0</span>
          </v-tab>
          <v-tab>تم إزالته</v-tab>
        </v-tabs>
        <v-card-title class="text-to-all py-2">
          <span class="ml-2">0</span>
          منتجات
          <v-spacer></v-spacer>
          <v-btn depressed class="text-to-all"> إضافة منتج جديد </v-btn>
        </v-card-title>
        <v-card-subtitle class="text-to-all py-2">
          بإمكانك تحميل 1000 منتج
        </v-card-subtitle>
        <!-- the products  -->
        <v-card
          flat
          tile
          style="height: calc(100vh - 242px)"
          class="mx-auto grey lighten-3 overflow-y-auto"
        >
          <v-tabs-items class="transparent px-1" v-model="tab">
            <v-tab-item>
              <v-row no-gutters>
                <v-col
                  v-for="(Car, i) in ShowRoomUserCars"
                  :key="i"
                  cols="12"
                  class="py-1"
                >
                  <v-card
                    :to="{
                      name: 'ProductsOnClickShowDetail',
                      params: {
                        carId: Car.id,
                      },
                    }"
                    height="100%"
                    class="overflow-hidden"
                    flat
                  >
                    <v-row no-gutters align="center" class="pa-0">
                      <!-- Products  imag and name  -->
                      <v-col cols="6">
                        <v-row align="center" no-gutters>
                          <!-- imag  -->
                          <v-col cols="4" lg="2" sm="2" md="2">
                            <v-avatar tile size="50">
                              <v-img
                                :src="getimageUrl(Car.folder, Car.image)"
                                :lazy-src="getimageUrl(Car.folder, Car.image)"
                                alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                              ></v-img>
                            </v-avatar>
                          </v-col>
                          <!-- name  -->
                          <v-col cols="8" lg="10" sm="10" md="10">
                            <v-card-text
                              class="pa-2 normal-text-edite text-truncate d-block"
                            >
                              {{ Car.company }} {{ Car.name }}
                            </v-card-text>
                          </v-col>
                        </v-row>
                      </v-col>
                      <!-- Car detail -->
                      <v-col>
                        <span class="price-cat text-end pa-1"> الفئه </span>
                      </v-col>
                      <v-col>
                        <span class="price-cat pa-1">
                          {{ Car.payment }}
                          <span class="mr-1">ريال</span>
                        </span>
                      </v-col>
                    </v-row>
                    <!--  -->
                  </v-card>
                </v-col>
              </v-row>
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </v-sheet>
      <v-row no-gutters> </v-row>
    </v-container>
  </div>
</template>
<script>
import ShowRoomUserCars from "../data-json/All-Car.json";
export default {
  name: "StoreProducts",
  components: {},
  data() {
    return {
      search: "",
      tab: null,
      items: ["Appetizers", "Entrees", "Deserts", "Cocktails"],
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.",
      ShowRoomUserCars,
      carId: this.$route.params.carId,
      selectedItem: 0,
    };
  },
  computed: {
    filteredStore: function () {
      return this.ShowRoomUserCars.filter((ShowRoomUserCars) => {
        return ShowRoomUserCars.name.match(this.search);
      });
    },
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
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheShowRoomPage {
  width: 100%;
  min-height: 100vh;
  .search {
    // margin: 0 auto;
    height: auto;
    width: 100%;
    font-family: $fontfamliy3;
    letter-spacing: 0px !important;
    @media (max-width: 600px) {
      width: 100%;
    }
  }
  .text-to-all {
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
  }
  .detail {
    font-family: $fontfamliy3;
    font-size: 13px !important;
  }
  .price-cat {
    font-family: $fontfamliy3;
    font-size: 13px !important;
  }
}
.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
::v-deep
  .v-tabs:not(.v-tabs--vertical):not(.v-tabs--right)
  > .v-slide-group--is-overflowing.v-tabs-bar--is-mobile:not(.v-slide-group--has-affixes)
  .v-slide-group__prev {
  display: none !important;
}
::v-deep .v-tab {
  font-size: 17px !important;
  font-weight: 600px;
  letter-spacing: 0 !important;
  font-family: $fontfamliy3;
}
</style>
