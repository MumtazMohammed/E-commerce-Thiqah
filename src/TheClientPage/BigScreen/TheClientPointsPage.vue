<template>
  <div class="UserAdd grey lighten-5">
    <v-container>
      <v-card
        class="mx-auto elevation-3 overflow--hidden"
        width="100%"
        color="transparent"
        height="150px"
        rounded="lg"
      >
        <v-row
          justify="center"
          align="center"
          style="flex-direction: column; height: 100%"
          no-gutters
          class="mt-"
        >
          <v-spacer></v-spacer>

          <span class="points-No-total"> 8 </span>
          <span class="points-No-text-total">نقطة</span>
          <v-spacer></v-spacer>
          <v-btn
            text
            elevation="0"
            color="grey darken-3"
            class="points-text-total my-2"
          >
            السجل
          </v-btn>
        </v-row>
      </v-card>
      <v-card-text class="get-text"> 1 نقطة تساوي 50 ريال </v-card-text>
      <v-card
        rounded="lg"
        flat
        class="my-auto mb-2 overflow--hidden"
        height="75"
        color="grey lighten-1"
      >
        <v-row style="height: 100%" align="center" no-gutters>
          <v-col class="pa-2" cols="12">
            <v-card-text class="card-text pa-0">
              شارك وأحصل على نقاط من خلال رابط الخاص قي الاسفل
            </v-card-text>
          </v-col>
          <!-- <v-col cols="1">
            <v-icon color="white">mdi-chevron-double-left</v-icon>
          </v-col> -->
        </v-row>
      </v-card>
      <v-card
        rounded="lg"
        flat
        class="my-auto mb-2 overflow--hidden"
        height="75"
        color="grey lighten-1"
      >
        <v-row style="height: 100%" align="center" no-gutters>
          <v-col class="pa-2" cols="11">
            <v-card-text class="card-text pa-0">
              تسوق على المنتجات المتميزه وأحصل على نقاط
            </v-card-text>
          </v-col>
          <v-col cols="1">
            <v-icon color="white">mdi-chevron-double-left</v-icon>
          </v-col>
        </v-row>
      </v-card>
      <v-card
        height="75"
        flat
        rounded="lg"
        class="mx-auto mb-2 overflow--hidden"
        color="grey lighten-1"
      >
        <v-row style="height: 100%" align="center" no-gutters>
          <v-col class="pa-2" cols="11">
            <v-card-text class="card-text pa-0">
              قم بي ترويج بعض منتجاتنا وأحصل على <span>300</span> نقطة عند قيام
              الطرف الثالث في الشراء
            </v-card-text>
          </v-col>
          <v-col cols="1">
            <v-icon color="white">mdi-chevron-double-left</v-icon>
          </v-col>
        </v-row>
      </v-card>
      <v-card
        class="mx-auto mt-3 overflow--hidden"
        width="100%"
        color="grey lighten-1"
        style="height: calc(100vh - 530px)"
        rounded="lg"
        flat
      >
        <v-row
          justify="center"
          align="center"
          style="flex-direction: column; height: 100%"
          no-gutters
          class="mt-"
        >
          <v-spacer></v-spacer>

          <v-card
            color=" grey lighten-2"
            flat
            width="90%"
            class="points-link pa-1"
          >
            http://localhost:8080/SmallScreenClientPointsPage/%D9%86%D9%82%D8%A7%D8%B7%D9%8A
          </v-card>
          <v-spacer></v-spacer>
          <v-btn text elevation="0" class="points-link-copy my-2 white">
            نسخ الرابط الخاص بك
          </v-btn>
        </v-row>
      </v-card>
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
  height: calc(100vh - 40px);
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0.5px;
    color: $fontcolorlinks !important;
    font-size: 16px !important;
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

  .get-text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0.5px;
    font-size: 15px !important;
    color: $fontcolor !important;
    font-weight: 600 !important;
    pointer-events: none;
  }
}
.points-text-total {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0.5px;
  font-weight: 600 !important;
  font-size: 14px !important;
}
.points-No-text-total {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0.5px;
  font-weight: 600 !important;
  font-size: 14px !important;
  color: $fontcolor;
  pointer-events: none;
}
.points-No-total {
  font-weight: 600 !important;
  font-size: 45px !important;
  color: $color-2;
  pointer-events: none;
}
.points-link {
  color: $fontcolor !important;
  display: inline-block;
  text-align: center;
  background-color: #fff;
  border-radius: 5px;
  pointer-events: none;
  // margin: 0 10px;
}
.points-link-copy {
  font-size: 16px !important;
  letter-spacing: 0.5px;
  font-family: $fontfamliy3 !important;
}
.card-text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-weight: 500 !important;
  font-size: 15px !important;
  color: $fontcolor;
  text-align: justify !important;
  line-height: 1.5 !important;
  span {
    font-family: sans-serif !important;
    font-size: 15px !important;
    letter-spacing: 0.5px;
    font-weight: 700 !important;
    margin: 0 3px;
    text-decoration: underline;
  }
}
</style>
