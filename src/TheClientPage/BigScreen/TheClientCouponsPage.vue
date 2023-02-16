<template>
  <div class="UserAdd">
    <v-container>
      <v-row justify="center" align="center" no-gutters class="px-3">
        <v-avatar class="profile" color="transparent" size="30">
          <v-img
            src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
          ></v-img>
        </v-avatar>
        <span class="store-name mr-1"> متجر بهلول </span>
        <v-spacer></v-spacer>
        <span class="coupons-date"> 02 / 04 / 2020 </span>
      </v-row>
      <v-row no-gutters>
        <v-col
          class="pa-2"
          md="6"
          lg="6"
          sm="6"
          cols="12"
          v-for="n in 3"
          :key="n"
        >
          <v-card flat color="#eee" class="card">
            <v-row no-gutters justify="center" class="main">
              <v-col style="border-left: 1px dashed grey" class="" cols="3">
                <v-row
                  align="center"
                  style="height: 100%"
                  justify="center"
                  no-gutters
                >
                  <v-avatar class="profile my-auto" color="grey" size="50">
                    <v-img
                      src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                    ></v-img>
                  </v-avatar>
                </v-row>
              </v-col>

              <v-col class="pr-1" cols="6">
                <v-card-subtitle class="text pa-1">
                  خصم <span class="mx-1 red--text"><span>20</span>%</span>
                </v-card-subtitle>
                <v-card-text class="pa-1 text">
                  أنفق
                  <span class="mx-1">
                    52<v-icon left size="17">mdi-currency-rial</v-icon>
                  </span>
                  كحد أدنى
                </v-card-text>
                <v-card-text class="pa-1 text">
                  متاح حتى
                  <span>10/2/2020</span>
                </v-card-text>
              </v-col>
              <v-col cols="3">
                <v-row
                  align="center"
                  style="height: 100%"
                  justify="center"
                  no-gutters
                >
                  <v-btn small fab dark class="white btn" elevation="0">
                    أخذ
                  </v-btn>
                </v-row>
              </v-col>
            </v-row>
            <ul class="Voucher">
              <li></li>
              <li></li>
              <li></li>
              <li></li>
              <li></li>
              <li></li>
            </ul>
          </v-card>
        </v-col>
      </v-row>
      <v-divider></v-divider>
      <span class="no-more">لا يوجد المزيد</span>
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
  min-height: 100vh;
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0.5px;
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

  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0px;
    font-size: 15px !important;
    color: #343434 !important;
    // font-weight: 600 !important;
    pointer-events: none;
  }
  .coupons-date {
    font-family: sans-serif !important;
    letter-spacing: 0px;
    font-size: 14px !important;
    color: #343434 !important;
    // font-weight: 600 !important;
    pointer-events: none;
  }
}
.text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  font-weight: 600 !important;

  @media (max-width: 600px) {
    font-size: 14px !important;
  }
}
.btn {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  font-size: 14px !important;
  margin: 0 auto !important;
  font-weight: 600;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
}
.Voucher {
  position: absolute;
  top: 0;
  left: -3px;
  padding: 5px 0;
  z-index: 5;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  li {
    list-style: none;
    width: 8px;
    height: 8px;
    background-color: #fff;
    border-radius: 50%;
    // border-right: 1px solid #42a5f5;
  }
}
.no-more {
  margin-top: 5px;
  text-align: center;
  display: block;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 13px !important;
  color: #f44336 !important;
}
</style>
