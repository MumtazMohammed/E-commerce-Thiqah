<template>
  <div class="SellerStore">
    <v-sheet
      style="overflow: hidden"
      class="overflow-hidden card-info"
      color=" py-0"
      dark
      rounded="lg"
    >
      <v-row class="row" no-gutters>
        <div
          style="display: flex; flex-direction: column; justify-content: center"
        >
          <!-- store image -->
          <v-avatar class="profile" color="grey" size="150" tile>
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <v-row no-gutters> </v-row>
        </div>
        <v-col class="info-lg" cols="3">
          <v-sheet
            color="transparent"
            style="display: flex; flex-direction: column"
            class="mr-3 fill-height"
          >
            <v-card-text class="pa-0 py-2 StoreName">
              إلكترونيات برو
            </v-card-text>
            <v-card color="white" max-width="170" class="overflow-hidden">
              <v-row class="fill-height" no-gutters>
                <span class="Storeauthorized"> ثقة مول </span>
                <span class="Storeauthorized-text">
                  <v-icon size="20" color="red">mdi-shield-check</v-icon>
                  بائع مرخص
                </span>
              </v-row>
            </v-card>
            <v-spacer></v-spacer>
            <v-btn-toggle
              background-color="transparent"
              tile
              borderless
              class="justify-center py-2"
              dense
            >
              <v-chip class="mx-1 px-6" text-color="white" color="red">
                <span class="btn">متابعة</span>
              </v-chip>
              <v-chip
                text-color="white"
                color="green accent-4"
                class="mx-1 px-5"
              >
                <span class="btn">مراسلة</span>
              </v-chip>
            </v-btn-toggle>
          </v-sheet>
        </v-col>
        <v-col class="info-sm">
          <div class="pa-2">
            <v-card-text class="pa-0 pb-2 StoreName">
              إلكترونيات برو
            </v-card-text>
            <v-card color="white" max-width="170" class="overflow-hidden">
              <v-row class="fill-height" no-gutters>
                <span class="Storeauthorized"> ثقة مول </span>
                <span class="Storeauthorized-text">
                  <v-icon size="20" color="red">mdi-shield-check</v-icon>
                  بائع مرخص
                </span>
              </v-row>
            </v-card>
          </div>
          <v-card-actions
            no-gutters
            style="align-items: center; height: 56% !important"
            class="fill-height justify-center py-1"
          >
            <v-chip class="mx-1" text-color="white" color="red">
              <span class="btn">متابعة</span>
            </v-chip>
            <v-chip text-color="white" color="green accent-4" class="mx-1">
              <span class="btn">مراسلة</span>
            </v-chip>
            <!-- store Info -->
            <v-dialog
              persistent
              no-click-animation
              v-model="dialog"
              max-width="300px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-chip
                  text-color="white"
                  color="blue"
                  v-bind="attrs"
                  v-on="on"
                  class="info-sm mx-1 btn-info-share"
                >
                  <span class="btn">تفاصيل</span>
                </v-chip>
              </template>
              <v-card>
                <v-card-title class="store-view">
                  <v-icon right size="23"> mdi-information-outline </v-icon>
                  حول المتجر
                </v-card-title>
                <v-divider></v-divider>
                <v-card-text style="height: 300px">
                  <ul class="pl-0 pr-0">
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-package
                      </v-icon>
                      المنتجات : <span class="deep-orange--text">44</span>
                    </li>
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-account-group
                      </v-icon>
                      المتابعين : <span class="deep-orange--text">44</span>
                    </li>
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-file-cancel
                      </v-icon>
                      معدل الإلغاء : <span class="deep-orange--text">44</span>
                    </li>
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-star
                      </v-icon>
                      تقييم المتجر : <span class="deep-orange--text">44</span>
                    </li>
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-account-clock
                      </v-icon>
                      انضم : <span class="deep-orange--text">44</span>
                    </li>
                    <li>
                      <v-icon color="grey  darken-1" right size="20">
                        mdi-forum-outline
                      </v-icon>
                      أداء الدردشة: : <span class="deep-orange--text">44</span>
                    </li>
                  </ul>
                </v-card-text>
                <v-divider></v-divider>
                <v-card-actions>
                  <v-btn
                    color="blue darken-1"
                    class="btn"
                    text
                    @click="dialog = false"
                  >
                    إغلاق
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-actions>
        </v-col>
        <v-spacer class="info-lg"></v-spacer>
        <div class="mr-3 info-lg">
          <ul class="pl-0 pr-6">
            <li>
              <v-icon right size="20"> mdi-package </v-icon>
              المنتجات : <span class="white--text">44</span>
            </li>
            <li>
              <v-icon right size="20"> mdi-account-group </v-icon>
              المتابعين : <span class="white--text">44</span>
            </li>
            <li>
              <v-icon right size="20"> mdi-file-cancel </v-icon>
              معدل الإلغاء : <span class="white--text">44</span>
            </li>
          </ul>
        </div>
        <div class="mr-3 ml-3 info-lg">
          <ul class="pl-0 pr-6">
            <li>
              <v-icon right size="20"> mdi-star </v-icon>
              تقييم المتجر : <span class="white--text">44</span>
            </li>
            <li>
              <v-icon right size="20"> mdi-account-clock </v-icon>
              انضم : <span class="white--text">44</span>
            </li>
            <li>
              <v-icon right size="20"> mdi-forum-outline </v-icon>
              أداء الدردشة: : <span class="white--text">44</span>
            </li>
          </ul>
        </div>
      </v-row>
    </v-sheet>
  </div>
</template>

<script>
import Services from "../data-json/showroom.json";
export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      Services,
      dialog: false,
      items: ["مقديشو", "كزبرا", "صلصة", "ثوم"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // computed: {
  //   getCarInfo() {
  //     let GetShowroomfeatured = [];
  //     for (let i = 0; i < this.featuredshowrooms.length; i++) {
  //       if (this.featuredshowrooms[i].featured == true) {
  //         GetShowroomfeatured.push(this.featuredshowrooms[i]);
  //       }
  //     }
  //     return GetShowroomfeatured;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.SellerStore {
  .card-info {
    @media (max-width: 700px) {
      // box-shadow: none !important;
    }
  }
  .StoreName {
    font-family: $fontfamliy3;
    font-size: 15px !important;
    letter-spacing: 0 !important;
  }
  .Storeauthorized {
    font-size: 12px !important;
    font-family: $fontfamliy3;
    background-color: red;
    padding: 0 8px;
    color: #fff;
    font-weight: 600;
  }
  .Storeauthorized-text {
    font-size: 12px !important;
    font-family: $fontfamliy3;
    font-weight: 600 !important;
    color: #000;
  }
}
.btn {
  letter-spacing: 0 !important;
  font-size: 16px !important;
  font-weight: 500 !important;
  font-family: $fontfamliy3 !important;
  // color: $fontcolor !important;
  @media (max-width: 600px) {
    font-size: 14px !important;
  }
}
ul {
  list-style: none !important;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  letter-spacing: 0 !important;
  font-size: 15px !important;
  font-weight: 600 !important;
  font-family: $fontfamliy3 !important;
  color: black !important;
  @media (max-width: 700px) {
    font-size: 16px !important;
  }
  span {
    margin-right: 5px;
  }
}
.store-view {
  font-size: 17px !important;
  font-weight: 600 !important;
  font-family: $fontfamliy3 !important;
  color: $fontcolorlinks;
  letter-spacing: 0 !important;
  @media (max-width: 600px) {
    font-size: 15px !important;
  }
  .v-icon {
    color: $color-2 !important;
  }
}
::v-deep.v-avatar.profile.rounded-0.grey {
  // border-radius: 3px !important;
  overflow: hidden !important;
  margin: auto 0;

  @media (max-width: 700px) {
    height: 133px !important;
    min-width: 130px !important;
    width: 130px !important;
    margin: 0;
    border-radius: 0px !important;
  }
  @media (max-width: 360px) {
    height: 160px !important;
    min-width: 180px !important;
    width: 180px !important;
    margin: 0;
    border-radius: 0px !important;
  }
}
.info-lg {
  @media (max-width: 700px) {
    display: none;
  }
}
.info-sm {
  display: none;
  @media (max-width: 700px) {
    display: block;
  }
}
.row {
  @media (max-width: 360px) {
    justify-content: center;
    align-items: center;
  }
}
.card-info {
  background: rgba(255, 255, 255, 0.2) !important;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1) !important;
  backdrop-filter: blur(5px) !important;
  -webkit-backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.3) !important;
}
</style>
