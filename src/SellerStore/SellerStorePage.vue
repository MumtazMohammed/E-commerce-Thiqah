<template>
  <div class="Sellerstore">
    <v-card flat tile class="overflow-hidden">
      <v-app-bar app color="#6A76AB" flat style="z-index: 8; overflow: hidden">
        <v-row no-gutters>
          <v-col cols="12">
            <!-- big screen  -->
            <v-container class="pa-0">
              <v-row no-gutters justify="center">
                <v-btn elevation="0" class="transparent" small fab>
                  <v-icon color="#ffff">mdi-dots-vertical</v-icon>
                </v-btn>
                <v-spacer></v-spacer>
                <v-card
                  height="40"
                  flat
                  width="75%"
                  rounded="sm"
                  style="overflow: hidden"
                  class="d-flex px-2 search-card align-center"
                >
                  <v-icon size="24" color="#fff" first.length>
                    mdi-magnify
                  </v-icon>
                  <v-text-field
                    flat
                    dense
                    hide-details
                    v-model="first"
                    dark
                    label="ابحث في هذا المتجر"
                    solo
                  ></v-text-field>
                </v-card>
                <!-- <v-btn>f</v-btn> -->
                <v-spacer></v-spacer>
                <v-btn elevation="0" class="transparent" small fab>
                  <v-icon color="#fff">mdi-arrow-left</v-icon>
                </v-btn>
              </v-row>
            </v-container>
          </v-col>
        </v-row>
        <template v-slot:extension>
          <v-tabs
            v-model="tab"
            slider-color="#eee"
            active-class="font-weight-bold "
            dark
          >
            <v-tab class="tabs-text"> المتجر </v-tab>
            <v-tab class="tabs-text"> المنتجات </v-tab>
            <v-tab class="tabs-text"> الفئة </v-tab>
            <v-tab class="tabs-text"> الحساب </v-tab>
          </v-tabs>
        </template>
      </v-app-bar>
      <v-sheet style="background-color: #f8f9fa">
        <v-sheet class="supporter"></v-sheet>
        <seller-info />
        <v-container class="pa-0 pt-3">
          <v-tabs-items style="min-height: " v-model="tab">
            <v-tab-item class="">
              <store-voucher />
              <about-store />
            </v-tab-item>
            <v-tab-item>
              <store-products />
            </v-tab-item>
            <v-tab-item style="min-height: calc(100vh - 305px)">
              <span>f</span>
            </v-tab-item>
            <v-tab-item>
              <span>d</span>
            </v-tab-item>
          </v-tabs-items>
        </v-container>
      </v-sheet>
    </v-card>
    <div class="hidden-md-and-up">
      <v-sheet height="50"></v-sheet>
      <FixedBottomNav />
    </div>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
import SellerInfo from "./SellerInfo.vue";
import StoreVoucher from "./StoreVoucher.vue";
import AboutStore from "./AboutStore.vue";
import StoreProducts from "./StoreProducts.vue";
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
export default {
  name: "ServicesPage",
  components: {
    SellerInfo,
    StoreVoucher,
    AboutStore,
    StoreProducts,
    FixedBottomNav,
  },
  data() {
    return {
      Services,
      first: "",
      filterdialog: null,
      tab: null,
      items: [
        { tab: "One", content: "Tab 1 Content" },
        { tab: "Two", content: "Tab 2 Content" },
        { tab: "Three", content: "Tab 3 Content" },
        { tab: "Four", content: "Tab 4 Content" },
        { tab: "Five", content: "Tab 5 Content" },
        { tab: "Six", content: "Tab 6 Content" },
        { tab: "Seven", content: "Tab 7 Content" },
        { tab: "Eight", content: "Tab 8 Content" },
        { tab: "Nine", content: "Tab 9 Content" },
        { tab: "Ten", content: "Tab 10 Content" },
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
.Sellerstore {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
}
::v-deep
  header.v-sheet.theme--light.v-toolbar.v-toolbar--flat.v-app-bar.v-app-bar--elevate-on-scroll.v-app-bar--fixed.v-app-bar--is-scrolled.grey.lighten-3 {
  z-index: 6 !important;
}
.btn-noti-cart {
  color: $color-2 !important;
  background-color: #eee;
  @media (max-width: 600px) {
    border: none !important;
    color: $color-2 !important;
  }
}
.tabs-text {
  font-family: $fontfamliy3;
  font-size: 15px;
  letter-spacing: 0 !important;
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border-width: 0;
}
::v-deep span.v-badge__badge {
  background-color: #eee !important;
  color: $color-2 !important;
  font-weight: 500;
  @media (max-width: 600px) {
    inset: auto calc(100% - 45px) calc(100% - 10px) auto !important;
  }
}
.btn-noti-cart-icon {
  font-size: 20px !important;
}
::v-deep
  header.v-sheet.theme--light.v-toolbar.v-app-bar.v-app-bar--elevate-on-scroll.v-app-bar--fixed.v-app-bar--is-scrolled.grey {
  z-index: 20;
}

::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3;
  font-size: 14px;
  color: #ffffff !important;
}
::v-deep label.v-label.theme--dark {
  font-family: $fontfamliy3;
  font-size: 14px;
  color: #ffffff !important;
}

::v-deep
  header.v-sheet.theme--light.v-toolbar.v-toolbar--absolute.v-toolbar--extended.v-toolbar--prominent.v-app-bar.v-app-bar--fade-img-on-scroll.v-app-bar--is-scrolled.v-app-bar--shrink-on-scroll {
  overflow: hidden;
}
::v-deep .v-input__slot {
  background-color: transparent !important;
}
::v-deep .v-toolbar__content {
  padding: 9px;
  justify-content: center;
}
::v-deep .v-tabs.elevation-0.v-tabs--align-with-title.theme--light {
  box-shadow: 0px 0 0 0 !important;
}
// ::v-deep .v-toolbar__extension {
//   padding: 0 !important;
// }
// ::v-deep .v-tab.v-tab--active {
//   margin: 0 !important;
// }
// ::v-deep .v-tab {
//   margin: 0 !important;
// }
.search-card {
  background: rgba(255, 255, 255, 0.2) !important;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1) !important;
  backdrop-filter: blur(5px) !important;
  -webkit-backdrop-filter: blur(5px);
}
::v-deep .v-banner__wrapper {
  padding: 0 !important;
  border: 0 !important;
}
::v-deep .v-banner__content {
  padding: 0 !important;
}

.supporter {
  height: 112px;
  @media (max-width: 960px) {
    height: 104px;
  }
}
</style>
