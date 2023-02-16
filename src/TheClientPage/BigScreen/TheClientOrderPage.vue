<template>
  <div class="UserAdd">
    <!-- car card  -->
    <v-container>
      <v-tabs
        rounded="dm"
        v-model="tab"
        slider-size="2"
        slider-color="#fc624d"
        class="rounded-sm overflow-hidden"
        centered
        grow
        background-color="grey lighten-3"
      >
        <v-tab href="#tab-1" active-class="links-active" class="links">
          الكل
        </v-tab>
        <v-tab href="#tab-2" active-class="links-active" class="links">
          الشحن
        </v-tab>
        <v-tab href="#tab-3" active-class="links-active" class="links">
          مكتمل
        </v-tab>
        <v-tab href="#tab-4" active-class="links-active" class="links">
          ملغي
        </v-tab>
      </v-tabs>
      <v-tabs-items v-model="tab" class="mt-2">
        <!-- All  -->
        <v-tab-item
          style="height: calc(100vh - 100px); overflow-y: scroll"
          value="tab-1"
          class="pb-4"
        >
          <v-col cols="12" class="py-1 px-0">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
              </v-card-actions>
              <v-card
                v-for="i in 3"
                :key="i"
                style="display: flex"
                class="pa-1 mb-1 py-2"
                flat
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-card-text
                    class="recount pa-0 pr-2 grey--text text--darken-1"
                  >
                    <span class="ml-1"> 2 </span>
                    ,
                    <span class="mx-1"> احمر</span>
                    ,
                    <span class="mx-1"> ee02121</span>
                    ,
                    <span class="mx-1"> (15 - 18) </span>
                  </v-card-text>
                  <v-card-text class="price pa-0 pr-2 red--text">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <v-card-actions class="pa-2">
                <v-btn block elevation="0" class="btn1"> الشراء مجدداً </v-btn>
              </v-card-actions>
            </v-sheet>
          </v-col>
          <v-col cols="12" class="py-1 px-0">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon class="grey--text" size="24">mdi-delete </v-icon>
                </v-btn>
              </v-card-actions>
              <v-card
                v-for="i in 2"
                :key="i"
                rounded="sm"
                flat
                style="display: flex"
                class="pa-1 mb-1 py-2"
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-card-text
                    class="recount pa-0 pr-2 grey--text text--darken-1"
                  >
                    <span class="ml-1"> 2 </span>
                    ,
                    <span class="mx-1"> احمر</span>
                    ,
                    <span class="mx-1"> ee02121</span>
                    ,
                    <span class="mx-1"> (15 - 18) </span>
                  </v-card-text>
                  <v-card-text class="price pa-0 red--text pr-2">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <v-card-actions class="pa-2 justify-center">
                <v-btn text elevation="0" class="rate-text"
                  >قيم الآن واحصل على 5 نقاط
                </v-btn>
                <!-- <v-spacer></v-spacer>
              <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span> -->
              </v-card-actions>
            </v-sheet>
          </v-col>
          <v-col :key="i" cols="12" class="py-1 px-0">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
                <v-btn small class="btn1 white--text grey" elevation="0">
                  إلغاء
                </v-btn>
              </v-card-actions>
              <v-card
                style="display: flex"
                class="pa-1 py-2"
                width="100%"
                flat
                rounded="sm"
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-card-text
                    class="recount pa-0 pr-2 grey--text text--darken-1"
                  >
                    <span class="ml-1"> 2 </span>
                    ,
                    <span class="mx-1"> احمر</span>
                    ,
                    <span class="mx-1"> ee02121</span>
                    ,
                    <span class="mx-1"> (15 - 18) </span>
                  </v-card-text>
                  <v-card-text class="price pa-0 pr-2 red--text">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <!-- Progress  -->
              <v-card-actions class="px-0">
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="blue white--text"
                    right
                    dark
                  >
                    mdi-check
                  </v-icon>
                  تم دفع ( <span>154</span> ريال)
                </v-card-text>
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="grey white--text"
                    right
                  >
                    mdi-check
                  </v-icon>
                  تم شحن المنتج
                </v-card-text>
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="grey white--text"
                    right
                  >
                    mdi-check
                  </v-icon>
                  تم توصيل المنتج
                </v-card-text>
              </v-card-actions>
            </v-sheet>
          </v-col>
        </v-tab-item>
        <!-- shipping order  -->
        <v-tab-item
          style="height: calc(100vh - 100px); overflow-y: scroll"
          value="tab-2"
          class="pb-4"
        >
          <v-col v-for="i in 5" :key="i" cols="12" class="py-1 px-0">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
                <v-btn small class="btn1 white--text grey" elevation="0">
                  إلغاء
                </v-btn>
              </v-card-actions>
              <v-card
                style="display: flex"
                class="pa-1 py-2"
                width="100%"
                flat
                rounded="sm"
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-row class="pr-2" no-gutters align="center">
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                  </v-row>
                  <v-card-text class="price pa-0 pr-2 red--text">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <!-- Progress  -->
              <v-card-actions class="px-0">
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="blue white--text"
                    right
                    dark
                  >
                    mdi-check
                  </v-icon>
                  تم دفع ( <span>154</span> ريال)
                </v-card-text>
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="grey white--text"
                    right
                  >
                    mdi-check
                  </v-icon>
                  تم شحن المنتج
                </v-card-text>
                <v-card-text
                  class="stepper-Info pa-0 grey--text text--darken-2"
                >
                  <v-icon
                    size="16"
                    style="border-radius: 50%; width: 18px; height: 18px"
                    class="grey white--text"
                    right
                  >
                    mdi-check
                  </v-icon>
                  تم توصيل المنتج
                </v-card-text>
              </v-card-actions>
            </v-sheet>
          </v-col>
        </v-tab-item>
        <!-- completed shipping order  -->
        <v-tab-item
          style="height: calc(100vh - 100px); overflow-y: scroll"
          value="tab-3"
          class="pb-4"
        >
          <v-col v-for="i in 3" :key="i" cols="12" class="py-1 px-0">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon class="grey--text" size="24">mdi-delete </v-icon>
                </v-btn>
              </v-card-actions>
              <v-card
                v-for="i in 2"
                :key="i"
                rounded="sm"
                flat
                style="display: flex"
                class="pa-1 mb-1 py-2"
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-row class="pr-2" no-gutters align="center">
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                  </v-row>
                  <v-card-text class="price red--text pa-0 pr-2">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <v-card-actions class="pa-2 justify-center">
                <v-btn text elevation="0" class="rate-text"
                  >قيم الآن واحصل على 5 نقاط
                </v-btn>
                <!-- <v-spacer></v-spacer>
              <span class="rate-text"> قيم الآن واحصل على 5 نقاط </span> -->
              </v-card-actions>
            </v-sheet>
          </v-col>
        </v-tab-item>
        <!-- cancelled order  -->
        <v-tab-item
          style="height: calc(100vh - 100px); overflow-y: scroll"
          value="tab-4"
          class="pb-4"
        >
          <v-col cols="12" class="py-1 px-0" v-for="i in 3" :key="i">
            <v-sheet rounded class="pa-1 grey lighten-2">
              <v-card-actions class="pa-0 align-center">
                <v-card-text class="pa-1 store-name">
                  <v-icon right>mdi-store-outline </v-icon>
                  وقت العطور
                </v-card-text>
                <v-btn icon>
                  <v-icon class="green--text" size="20">mdi-message </v-icon>
                </v-btn>
              </v-card-actions>
              <v-card
                v-for="i in 3"
                :key="i"
                style="display: flex"
                class="pa-1 mb-1 py-2"
                flat
              >
                <v-avatar class="avatar" rounded size="60" color="#fff">
                  <v-img
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  ></v-img>
                </v-avatar>
                <div>
                  <v-card-text
                    class="title pa-0 pr-2 grey--text text--darken-2"
                  >
                    مـازدا مازدا3
                  </v-card-text>
                  <v-row class="pr-2" no-gutters align="center">
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="grey--text d-block pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px" class="ml-1">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                    <v-sheet max-width="70px">
                      <v-card-text
                        class="d-block grey--text pa-0 text-truncate"
                      >
                        (15 - 18)
                      </v-card-text>
                    </v-sheet>
                  </v-row>
                  <v-card-text class="price pa-0 pr-2 red--text">
                    10254<span class="mr-1">ريال</span>
                  </v-card-text>
                </div>
                <!-- <v-card-title class="recount pa-0 pr-2 grey--text text--darken-1">
                *عدد (<span>55</span>)
              </v-card-title> -->
              </v-card>
              <v-card-actions class="pa-2">
                <v-btn block elevation="0" class="btn1"> الشراء مجدداً </v-btn>
              </v-card-actions>
            </v-sheet>
          </v-col>
        </v-tab-item>
      </v-tabs-items>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "UserAdd",
  components: {},
  data() {
    return {
      text: "هل أنت متأكد من حذف الأعلان.",
      tab: null,
    };
  },
  methods: {
    customFilter(item, queryText) {
      const textOne = item.name.toLowerCase();
      const textTwo = item.abbr.toLowerCase();
      const searchText = queryText.toLowerCase();

      return (
        textOne.indexOf(searchText) > -1 || textTwo.indexOf(searchText) > -1
      );
    },
    save() {
      this.hasSaved = true;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.UserAdd {
  width: 100%;
  // padding: $padding;
  min-height: calc(100vh - 60px);

  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 17px !important;
  }
  .recount {
    font-family: sans-serif !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
    font-weight: 600;
    pointer-events: none;
  }
  .price {
    font-family: sans-serif !important;
    color: $fontcolor;
    font-size: 18px !important;
    font-weight: 700;
    pointer-events: none;
  }
  .links {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600;
    font-size: 15px !important;
  }
  .links:hover {
    color: $color-2 !important;
  }
  .links-active {
    color: $color-2 !important;
  }
  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    pointer-events: none;
    .v-icon {
      color: $fontcolorlinks;
      font-size: 20px !important;
    }
  }
  .btn1 {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 14px !important;
    color: #1e88e5;
    // background-color: $color-2 !important;
  }
  .rate-text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    pointer-events: none;
    font-size: 14px !important;
    color: $color-2;
    pointer-events: none;
  }
}
.stepper-Info {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-weight: 600 !important;
  font-size: 13px !important;
  color: $fontcolorlinks !important;
  text-align: center;
  pointer-events: none;
}
::v-deep .theme--light.v-stepper .v-stepper__step--complete .v-stepper__label {
  color: $color-2 !important;
}
::v-deep .theme--light.v-tabs .v-tab:hover:before {
  opacity: 0 !important;
}
</style>
