<template>
  <div class="TheClientCartPage">
    <v-app-bar flat class="mb-5" app>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="22">mdi-cart-plus</v-icon>
        سلة التسوق
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-sheet
      color="transparent"
      style="height: calc(100vh - 105px); overflow-y: scroll"
    >
      <v-container class="mt-14 py-1 px-1">
        <v-col v-for="i in 2" :key="i" cols="12" class="py-1 px-2">
          <v-sheet rounded class="pa-1 grey lighten-2">
            <v-card-actions class="pa-0">
              <v-checkbox
                hide-details
                value="1"
                class="ma-0 pa-0"
                v-model="checkbox"
              ></v-checkbox>
              <v-card-text class="pa-1 store-name">
                <v-icon right>mdi-store-outline </v-icon>
                وقت العطور
              </v-card-text>
              <v-btn icon>
                <v-icon class="green--text" size="20">mdi-message </v-icon>
              </v-btn>
              <v-btn small class="mr-0 store-name" elevation="0"> حذف </v-btn>
            </v-card-actions>
            <v-card
              v-for="i in 3"
              :key="i"
              rounded="sm"
              color="white"
              flat
              class="mb-2"
            >
              <v-row
                no-gutters
                class="justify-start flex-wrap align-start pa-0"
              >
                <v-col cols="3" class="text--center">
                  <v-img
                    height="95"
                    class="my-auto"
                    src="@/assets/Mazda/mazda1.jpg"
                    alt="@/assets/Hyundai/image2.jpg"
                  >
                    <v-checkbox
                      hide-details
                      value="1"
                      class="ma-0 pa-0"
                      v-model="checkbox"
                    ></v-checkbox>
                  </v-img>
                </v-col>
                <v-col cols="9">
                  <div>
                    <v-card-text
                      class="recount text-truncate d-block pa-1 pr-2 grey--text text--darken-2"
                    >
                      مـازدا مازدا3 مـازدا مـازدا مازدا3
                    </v-card-text>
                    <v-card
                      @click="sheet = !sheet"
                      flat
                      tile
                      class="recount pa-1"
                    >
                      <v-row no-gutters align="center">
                        <v-sheet max-width="70px" class="ml-1">
                          <v-card-text class="d-block pa-0 text-truncate">
                            (15 - 18)
                          </v-card-text>
                        </v-sheet>
                        <v-sheet max-width="70px" class="ml-1">
                          <v-card-text class="d-block pa-0 text-truncate">
                            (15 - 18)
                          </v-card-text>
                        </v-sheet>
                        <v-sheet max-width="70px" class="ml-1">
                          <v-card-text class="d-block pa-0 text-truncate">
                            (15 - 18)
                          </v-card-text>
                        </v-sheet>
                        <v-sheet max-width="70px">
                          <v-card-text class="d-block pa-0 text-truncate">
                            (15 - 18)
                          </v-card-text>
                        </v-sheet>
                        <v-spacer></v-spacer>
                        <v-icon size="22">mdi-chevron-down</v-icon>
                      </v-row>
                    </v-card>
                    <v-row align="center" no-gutters class="py-1">
                      <span class="price d-block my-auto pa-0 px-2">
                        10254
                        <span class="text-center">ريال</span>
                      </span>
                      <v-btn icon color="grey ">
                        <v-icon>mdi-delete</v-icon>
                      </v-btn>
                    </v-row>
                  </div>
                </v-col>
              </v-row>
            </v-card>
          </v-sheet>
        </v-col>
      </v-container>
    </v-sheet>
    <!-- edit the order   -->
    <v-bottom-sheet v-model="sheet">
      <v-sheet class="text-center pt-1" height="auto">
        <v-row no-gutters>
          <v-col cols="12">
            <v-card-actions class="justify-start py-0 align-start">
              <v-avatar tile size="70" color="transparent">
                <v-img
                  contain
                  max-width="85"
                  class="my-auto"
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                ></v-img>
              </v-avatar>
              <div>
                <p
                  class="Product-name-text grey--text text--darken-1 d-inline-block text-truncate mr-2 ma-0 mt-1"
                >
                  مـازدا مازدا3
                </p>
                <p
                  style="font-size: 17px; font-weight: 600"
                  class="mb-1 mr-2 d-block text-start red--text"
                >
                  10254
                </p>
              </div>
            </v-card-actions>
          </v-col>
        </v-row>
        <v-card flat color="" class="pa-2 pt-0">
          <v-card-actions>
            <p class="Colors-text mb-0 grey--text text--darken-1">الألوان :</p>
            <v-chip-group
              class="justify-center"
              active-class="select-img"
              tile
              column
            >
              <v-chip label v-for="x in 5" :key="x" class="px-1">
                <v-img
                  width="50"
                  height="30"
                  @click="
                    ActiveImage = getimageUrl(getCarInfo.folder, singleImage)
                  "
                  src="@/assets/Mazda/mazda1.jpg"
                  alt="@/assets/Hyundai/image2.jpg"
                />
              </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions>
            <p class="Colors-text grey--text text--darken-1">الألوان :</p>
            <v-chip-group active-class="select" column class="mx-auto">
              <v-chip active small> Elevator </v-chip>
              <v-chip small> Washer / Dryer </v-chip>
              <v-chip small> Fireplace </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions>
            <p class="Colors-text grey--text text--darken-1">الألوان :</p>
            <v-chip-group active-class="select" column class="mx-auto">
              <v-chip active small> Elevator </v-chip>
              <v-chip small> Washer / Dryer </v-chip>
              <v-chip small> Fireplace </v-chip>
            </v-chip-group>
          </v-card-actions>
          <v-card-actions>
            <p class="Colors-text mb-0 grey--text text--darken-1">العدد :</p>
            <v-card
              style="overflow: hidden; margin: 0 auto"
              outlined
              max-width="150"
            >
              <v-card-actions class="pa-0">
                <v-btn
                  class="px-1"
                  tile
                  elevation="0"
                  height="30"
                  min-width="35"
                  @click="Quantity++"
                >
                  <v-icon size="18" color="grey darken-2"> mdi-plus </v-icon>
                </v-btn>
                <v-text-field
                  solo
                  dense
                  flat
                  v-model="Quantity"
                  hide-details
                  class="text-center"
                  type="number"
                ></v-text-field>
                <v-btn
                  class="px-1"
                  tile
                  elevation="0"
                  height="30"
                  min-width="35"
                  @click="Quantity--"
                >
                  <v-icon size="18" color="grey darken-2"> mdi-minus </v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-card-actions>
        </v-card>
        <!-- <v-divider class="mb-2"></v-divider> -->
        <v-card-actions class="justify-center pt-0">
          <v-btn elevation="0" width="120px" class="add-chat"> إضــافـة </v-btn>
          <v-btn
            @click="sheet = false"
            elevation="0"
            width="120px"
            class="add-chat"
          >
            إلـغـاء
          </v-btn>
        </v-card-actions>
      </v-sheet>
    </v-bottom-sheet>
    <!-- select all  -->
    <v-sheet class="sheet px-2" height="105">
      <v-card-actions
        class="pa-0"
        style="width: 100%; justify-content: space-between; height: 100%"
      >
        <v-card
          flat
          tile
          style="display: flex; flex-direction: column; justify-content: center"
          height="100%"
        >
          <v-checkbox
            hide-details
            class="ma-0 pa-0"
            v-model="checkbox"
            label="أختيار الكل"
          ></v-checkbox>
          <v-card-text class="pa-1 pr-2 check-out">
            إجمالي الطلبات (
            <span class="mx-1 red--text">{{ checkbox }}</span> )
            <span class="mx-1 green--text">0.00</span> ريال
          </v-card-text>
        </v-card>
        <v-btn elevation="0" class="CheckOut">شراء</v-btn>
      </v-card-actions>
    </v-sheet>
  </div>
</template>
<script>
export default {
  name: "TheClientCartPage",
  data() {
    return {
      checkbox: 0,
      value: "recent",
      sheet: false,
      Quantity: 1,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.TheClientCartPage {
  width: 100%;
  min-height: 40vh;
  // padding: $padding;
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-size: 15px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $color-2 !important;
      margin-left: 5px;
    }
  }

  .recount {
    font-family: sans-serif !important;
    letter-spacing: 0;
    font-weight: 600;
    color: $fontcolor;
    font-size: 15px !important;
    // pointer-events: none;
  }
  .price {
    font-family: sans-serif !important;
    color: $color-2;
    font-size: 19px !important;
    font-weight: 700;
  }

  .check-out {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 15px !important;
    color: $fontcolorlinks;
  }
  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 600 !important;
    font-size: 13px !important;
    color: $fontcolorlinks;
    .v-icon {
      color: $fontcolorlinks !important;
      font-size: 20px !important;
    }
  }
  .chat-icon {
    color: #fff !important;
  }
}
::v-deep .theme--light.v-btn:hover:before {
  opacity: 0;
}
::v-deep .theme--light.v-btn:focus:before {
  background-color: transparent;
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-weight: 500 !important;
  font-size: 13.5px !important;
}
::v-deep .v-input--selection-controls__ripple {
  display: none;
}
::v-deep .v-input__slot {
  width: fit-content;
}
.sheet {
  position: fixed;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: 5;
  border-top: 1px solid #eee !important;
}
.CheckOut {
  background-color: $color-2 !important;
  font-family: $fontfamliy3;
  letter-spacing: 0;
  color: #fff !important;
  font-size: 14px !important;
}
::v-deep .v-chip-group .v-slide-group__content {
  padding: 0 !important;
  justify-content: center;
}
// edit order
.select-img {
  box-shadow: 0 0 0px 3px $color-2 !important;
  color: #fff !important;
}
.select {
  background-color: $color-2;
  // box-shadow: 0 0 2px 2px $color-2 !important;
  color: #fff !important;
}
.Colors-text {
  font-family: $fontfamliy3 !important;
  font-size: 16px;
  font-weight: 600;
  display: block;
  text-align: start;
  margin-bottom: 0;
  pointer-events: none;
  @media (max-width: 600px) {
    font-size: 14px !important;
  }
}
.Product-name-text {
  font-family: $fontfamliy3 !important;
  font-size: 16px;
  font-weight: 400;
  pointer-events: none;
}
::v-deep button.add-chat {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolor;
  font-size: 14px;
  font-weight: 600;
}
::v-deep .v-text-field.v-text-field--solo.v-input--dense > .v-input__control {
  min-height: 30px !important;
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  text-align: center;
}
::v-deep .v-chip--disabled {
  opacity: 1 !important;
}
</style>
