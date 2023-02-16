<template>
  <div class="TheClientCartPage grey lighten-3">
    <v-app-bar class="mb-5" app flat>
      <v-toolbar-title class="toolbar-title">
        <v-icon size="22" right>mdi-message-draw</v-icon>
        تقييماتي
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-container class="mt-14 pa-2">
      <v-sheet v-for="item in 3" :key="item" class="pa-2 mb-2">
        <v-row
          align="center"
          justify="center"
          no-gutters
          class="mb-2 store-name"
        >
          <v-avatar class="profile ml-2" color="transparent" size="25">
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <span> عبد الصمد </span>
          <v-spacer></v-spacer>
          <span>15 / 01 / 2022</span>
        </v-row>
        <v-card flat class="blue-grey lighten-5 mb-2">
          <v-row align="center" no-gutters class="pa-0">
            <v-img
              contain
              max-width="60"
              src="@/assets/Mazda/mazda1.jpg"
              alt="@/assets/Hyundai/image2.jpg"
            ></v-img>

            <span class="recount d-block pr-2 grey--text text--darken-2">
              مـازدا مازدا3
            </span>
          </v-row>
        </v-card>
        <v-card flat class="blue-grey lighten-5 mb-1">
          <v-card-title class="store-name light-blue--text py-2">
            تقيمك على المنتج :
            <v-spacer></v-spacer>
            <v-rating
              color="warning"
              dense
              empty-icon="mdi-star-outline"
              full-icon="mdi-star"
              length="5"
              readonly
              size="15"
              value="4"
            ></v-rating>
          </v-card-title>
          <v-card-text class="seller-com">
            إذا كنت تريد تصميم صفحة ويب أو موقع إلكتروني يجب عليك أولاً تعلم
            كتابة الأكواد الأساسية قبل الشروع في كتابة الأوامر والأكواد
            الثانوية.
          </v-card-text>
        </v-card>
        <v-card flat class="blue-grey lighten-5">
          <v-card-subtitle
            class="store-name light-blue--text text--darken-2 py-2"
          >
            رد البائع :
          </v-card-subtitle>
          <v-card-text class="seller-com">
            إذا كنت تريد تصميم صفحة ويب أو موقع إلكتروني يجب عليك أولاً تعلم
            كتابة الأكواد الأساسية قبل الشروع في كتابة الأوامر والأكواد
            الثانوية.
          </v-card-text>
        </v-card>
      </v-sheet>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "TheClientCartPage",
  data() {
    return {
      checkbox: 0,
      value: "recent",
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.TheClientCartPage {
  width: 100%;
  min-height: 100vh;
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
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    color: $fontcolor;
    font-size: 13px !important;
    font-weight: 600;
  }

  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0;
    font-weight: 500 !important;
    font-size: 14px !important;
    color: $fontcolorlinks;
    .v-icon {
      color: $color-2 !important;
      font-size: 20px !important;
    }
  }
  .seller-com {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    line-height: 1.5;
    font-size: 14px !important;
    color: $fontcolor !important;
  }
}
::v-deep
  button.v-icon.notranslate.v-icon--link.mdi.mdi-star-outline.theme--light.accent--text {
  color: grey !important;
}
</style>
