<template>
  <!-- search for showroom -->
  <div class="search-wrapping">
    <v-container class="search-containers hidden-sm-and-down">
      <v-row no-gutters class="justify-space-between" align="center">
        <!-- customiza search for small screen -->
        <router-link router to="/">
          <v-row no-gutters fill-height justify="center" align="center">
            <h3 class="logo-text">ثــــقـــة لتجارة الأكترونية</h3>
            <v-icon
              style="
                background-color: #fc624d;
                padding: 3px;
                border-radius: 50%;
                color: white;
              "
              left
              size="22"
            >
              mdi-shopping
            </v-icon>
          </v-row>
        </router-link>

        <v-col cols="4">
          <v-card-actions class="justify-end pa-0">
            <!-- cart shopping  -->
            <v-badge bordered left overlap content="425" class="mx-3">
              <v-btn
                :to="{
                  name: 'TheClientCartPage',
                  params: { Cart: 'سلة التسوق ' },
                }"
                depressed
                class="btn-noti-cart deep-orange lighten-5"
                icon
                large
              >
                <v-icon class="btn-noti-cart-icon">mdi-cart</v-icon>
              </v-btn>
            </v-badge>
            <!-- notification btn -->
            <!-- <v-badge bordered left overlap content="445" class="mx-3">
              <v-btn  depressed class="btn-noti-cart" icon>
                <v-icon class="btn-noti-cart-icon">mdi-bell-outline</v-icon>
              </v-btn>
            </v-badge> -->
          </v-card-actions>
        </v-col>
      </v-row>
      <v-row no-gutters justify="center" class="mt-2">
        <v-card
          max-width="700px"
          color="transparent"
          class="search rounded-a-0"
        >
          <!-- customiza search -->
          <v-card-actions class="pa-0 overflow-hidden">
            <v-text-field
              class="rounded-b-0 rounded-tl-0"
              v-model="search"
              solo
              flat
              dense
              label="على ماذا تبحث... "
              hide-details="true"
              background-color="#eee"
              @focus="ShowSerachCardvisble = true"
            ></v-text-field>
            <!-- delete text  -->
            <v-btn
              v-if="search.length > 0 && ShowSerachCardvisble"
              elevation="0"
              class="close ma-0"
              @click="reset()"
            >
              <v-icon class="">mdi-close</v-icon>
            </v-btn>
            <v-icon v-else class="close">mdi-magnify</v-icon>
          </v-card-actions>

          <!-- search stroe names  -->
          <v-expand-transition>
            <v-card
              v-if="search.length > 0 && ShowSerachCardvisble"
              max-width="100%"
              color="white"
              flat
              class="mx-auto white Featured-card overflow-hidden"
            >
              <v-list-item
                router
                @click="ShowSerachCardvisble = false"
                :to="{
                  name: 'ShowTheProduct',
                  params: {
                    carName: CarData.name,
                    carShape: CarData.Shape,
                    carId: CarData.id,
                    Company: CarData.folder,
                  },
                }"
                v-for="CarData in filteredStore"
                :key="CarData.id"
              >
                <!-- <v-list-item-avatar>
                  <v-avatar size="50" color="#424342">
                    <v-img
                      contain
                      :src="getimageUrl(CarData.folder, CarData.image)"
                      :lazy-src="getimageUrl(CarData.folder, CarData.image)"
                    >
                    </v-img>
                  </v-avatar>
                </v-list-item-avatar> -->
                <v-list-item-content>
                  <v-list-item-title v-text="CarData.name"> </v-list-item-title>
                  <!-- <v-spacer></v-spacer>
                  <v-list-item-subtitle>
                    {{ CarData.id }}
                  </v-list-item-subtitle> -->
                </v-list-item-content>
              </v-list-item>
              <v-card-title class="not-found" v-if="filteredStore.length < 1">
                نتأسف لا يوجد اي منتج بهذا الاسم
                <span class="mx-2 red--text"> {{ search }} </span>
              </v-card-title>
            </v-card>
          </v-expand-transition>
        </v-card>
      </v-row>
    </v-container>
    <!-- small screen nave  -->
    <v-card class="hidden-md-and-up supporter" flat></v-card>
    <v-app-bar class="hidden-md-and-up" app color="#f8f9fa" fixed flat>
      <v-row class="px-2" no-gutters align="center">
        <v-col cols="7">
          <v-dialog
            v-model="dialog"
            fullscreen
            hide-overlay
            transition="fade-transition"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-card
                v-bind="attrs"
                v-on="on"
                flat
                width="100%"
                height="35px"
                color="#eee"
                class="search-small-screen mr-1 ml-3"
              >
                <v-row
                  align="center"
                  style="height: 100%"
                  no-gutters
                  class="pa-0"
                >
                  <v-icon color="grey lighten-1" size="20" class="mr-1"
                    >mdi-magnify</v-icon
                  >
                  <span class="pa-1 icon-small-screen-text">
                    على ماذا تبحث...
                  </span>
                </v-row>
              </v-card>
            </template>
            <v-card>
              <v-toolbar tile color="transparent">
                <v-card width="100%" flat color="#eee" class="pr-2">
                  <v-card-actions class="pa-0">
                    <v-text-field
                      placeholder="على ماذا تبحث..."
                      solo
                      @focus="SearchClick"
                      v-model="search"
                      flat
                      prepend-icon="mdi-magnify"
                      hide-details
                      dense
                      class="px-0"
                    ></v-text-field>
                    <!-- delete text  -->
                    <v-btn v-if="search.length > 0" small icon @click="reset()">
                      <v-icon size="20" class="red--text">mdi-close</v-icon>
                    </v-btn>
                    <v-btn icon dark @click="dialog = false">
                      <v-icon color="primary" class="close-search-dig"
                        >mdi-arrow-left</v-icon
                      >
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-toolbar>
              <v-expand-transition>
                <div v-if="search.length > 0">
                  <v-list-item
                    class="search-list-dig"
                    outlined
                    router
                    @click="dialog = false"
                    :to="{
                      name: 'ViewCar',
                      params: {
                        carName: CarData.name,
                        carShape: CarData.Shape,
                        carId: CarData.id,
                        Company: CarData.folder,
                      },
                    }"
                    v-for="CarData in filteredStore"
                    :key="CarData.id"
                  >
                    <v-list-item-content>
                      <v-list-item-title v-text="CarData.name">
                      </v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                  <v-card-title
                    class="not-found"
                    v-if="filteredStore.length < 1"
                  >
                    لا يوجد (<span class="mx-2 red--text">
                      {{ search }}
                    </span>
                    )
                  </v-card-title>
                </div>
              </v-expand-transition>
            </v-card>
          </v-dialog>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="4">
          <v-row justify="space-around" no-gutters class="pa-0 pt-1">
            <!-- cart shopping  -->

            <v-badge bordered left overlap content="425" class="">
              <v-btn
                :to="{
                  name: 'SmallScreenClientCartPage',
                  params: { Cart: 'سلة التسوق ' },
                }"
                depressed
                class="btn-noti-cart deep-orange lighten-5"
                fab
                small
              >
                <v-icon>mdi-cart</v-icon>
              </v-btn>
            </v-badge>
            <!-- notification btn -->
            <v-badge bordered left overlap content="445" class="">
              <v-btn
                :to="{
                  name: 'SmallScreenNotification',
                  params: { Notfication: 'الأشعارات' },
                }"
                exact-path
                depressed
                class="btn-noti-cart deep-orange lighten-5"
                fab
                small
              >
                <v-icon> mdi-bell </v-icon>
              </v-btn>
            </v-badge>
          </v-row>
        </v-col>
      </v-row>
    </v-app-bar>
    <!-- <div class="TheCategories">
      <TheCategories />
    </div> -->
  </div>
  <!--end search  -->
</template>
<script>
import CarData from "../data-json/All-Car.json";
// import TheCategories from "../Search/TheCategories.vue";

export default {
  name: "showroom",
  components: {},
  data() {
    return {
      CarData,
      SearchClick: false,
      dialog: false,
      e1: "جميع المحافظات",
      showrooms: this.$attrs.showrooms,
      ShowRoomName: this.$route.params.ShowRoomName,
      // showroom search
      search: "",
      select: null,
      benched: 0,
      ShowSerachCard: "",
      ShowSerachCardvisble: false,
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
      return this.CarData.filter((CarData) => {
        return CarData.name.match(this.search);
      });
    },
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1);
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
a {
  text-decoration: none;
}
.logo-text {
  font-family: $fontfamliy3;
  color: $color-2 !important;
  font-weight: 600 !important;
  font-size: 17px !important;
}
.search-wrapping {
  background-color: $backgroundcard;
  @media (max-width: 600px) {
    background-color: #fff;
  }
}

::v-deep label.v-label.theme--light {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
::v-deep .v-btn--icon.v-size--default {
  @media (max-width: 600px) {
    height: 30px;
    width: 30px;
  }
}
.search {
  height: auto;
  width: 100%;
  font-family: $fontfamliy;
  letter-spacing: 0px;
  padding: 0px;
  box-shadow: 0px 0px 0px 1px $color-3 !important;
  @media (max-width: 600px) {
    display: none;
  }
}

.v-text-field::v-deep .v-label.theme--light {
  font-family: $fontfamliy3 !important;
  font-weight: 500;
  font-size: 14px;
  color: grey;
}
.v-text-field::v-deep input#input-66 {
  font-family: $fontfamliy !important;
  font-weight: 500;
}
.search-container {
  @media (max-width: 600px) {
    padding-right: 5px;
    padding-left: 5px;
  }
}
.Featured-card {
  position: absolute;
  top: calc(0px + 40px);
  width: 100%;
  height: auto;
  right: 0;
  z-index: 5555;
  .Featured-text {
    font-family: $fontfamliy !important;
    font-size: 15px;
    font-weight: 500;
  }
}
.close {
  height: 38px !important;
  min-width: 45px !important;
  background-color: transparent !important;
  color: $color-2 !important;
  // color: $fontcolorsm !important;
  border-radius: 0px;
}
.v-select {
  font-family: $fontfamliy !important;
  height: 50px;
}
.v-select::v-deep .v-select__selection--comma {
  font-family: $fontfamliy !important;
  height: 22px;
}
.not-found {
  font-size: 14px !important;
  font-family: $fontfamliy3 !important;
}
::v-deep .v-image__image.v-image__image--cover {
  background-position: top !important;
}
.btn-noti-cart {
  color: $color-2 !important;
  // background-color: #eee;
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border-width: 0;
}
::v-deep span.v-badge__badge {
  color: #fff !important;
  background-color: $color-2 !important;
  // min-width: 15px;
  height: 18px;
  // padding: 5px;
  // display: flex;
  // justify-content: center;
  // align-items: center;
  border: none;
  // font-size: 13px !important;
  @media (max-width: 600px) {
    font-size: 11px !important;
  }
}

::v-deep .v-toolbar__content .v-btn.v-btn--icon.v-size--default {
  width: 37px !important;
  height: 37px !important;
}

.icon-small-screen-text {
  font-size: 13px !important;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
}
.TheCategories {
  @media (max-width: 600px) {
    display: none;
  }
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input::placeholder {
  font-size: 15px !important;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  letter-spacing: 0px !important;
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  font-size: 15px;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  letter-spacing: 0px !important;
}
::v-deep .v-input__slot {
  background-color: transparent !important;
}
::v-deep .v-list-item .v-list-item__title {
  line-height: 1.6;
  font-size: 14px !important;
  color: $fontcolor !important;
  letter-spacing: 0px !important;
  font-family: $fontfamliy3;
  font-weight: 600;
}
::v-deep .v-toolbar__content {
  padding: 4px !important;
}
.close-search-dig {
  color: $color-2 !important;
}
.search-list-dig {
  color: #fff !important;
  border-bottom: 1px solid #eee;
}
.supporter {
  height: 16px;
  @media (max-width: 600px) {
    height: 56px;
  }
}
</style>
