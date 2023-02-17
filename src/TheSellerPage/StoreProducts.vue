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
      <v-sheet
        class="pa-sm-5 pa-2 pa-md-5 pa-xl-5 transparent"
        outlined
        max-width="100%"
        min-height="700"
      >
        <v-row no-gutters>
          <!-- search  -->
          <v-col cols="12" md="7" lg="7">
            <v-card color="" outlined class="search overflow-hidden">
              <v-text-field
                class="rounded-sm elevation-0"
                v-model="search"
                solo
                flat
                clearable
                label="  أبحث عن أسم المنتج ؟ "
                hide-details="true"
                background-color="#fff"
                append-icon="mdi-store-search-outline"
                @focus="ShowSerachCardvisble = true"
              ></v-text-field>
            </v-card>
          </v-col>
          <v-col cols="12" md="5" lg="5">
            <v-card-actions class="pa-0">
              <v-chip-group
                v-model="selection"
                active-class="blue--text "
                mandatory
                show-arrows
                center-active
                class="justify-center"
              >
                <v-chip outlined class="text">الكل</v-chip>
                <v-chip outlined class="text">مباع</v-chip>
                <v-chip outlined class="text">موقف</v-chip>
                <v-chip outlined class="text">متميز</v-chip>
              </v-chip-group>
              <v-spacer></v-spacer>
              <v-chip
                outlined
                class="text"
                :to="{
                  name: 'AddNewProducts',
                  params: { AddNewCar: 'إضافة منتج جديد' },
                }"
              >
                إضافة منتج
                <v-icon right size="17">mdi-folder-plus-outline</v-icon>
              </v-chip>
            </v-card-actions>
          </v-col>
          <v-col
            v-for="(Car, i) in ShowRoomUserCars"
            :key="i"
            cols="12"
            class="my-1"
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
              <v-card-actions>
                <!-- Products main Img  -->
                <v-avatar rounded class="ml-2" size="70">
                  <v-img
                    contain
                    :src="getimageUrl(Car.folder, Car.image)"
                    :lazy-src="getimageUrl(Car.folder, Car.image)"
                    alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                  ></v-img>
                </v-avatar>
                <!-- Car detail -->
                <span class="detail pa-1 text-truncate">
                  <span>{{ Car.company }} {{ Car.name }}</span>
                </span>
                <v-spacer></v-spacer>
                <span class="price-cat text-end pa-1"> الفئه </span>
                <v-spacer></v-spacer>
                <span class="price-cat pa-1">
                  {{ Car.payment }}
                  <span class="mr-1">ريال</span>
                </span>
              </v-card-actions>
              <!--  -->
            </v-card>
          </v-col>
        </v-row>
      </v-sheet>
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
  .text {
    background-color: $color-2;
    font-family: $fontfamliy3;
    color: $fontcolorlinks;
    letter-spacing: 0px !important;
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
::v-deep .v-slide-group__content {
  justify-content: center;
}
</style>
