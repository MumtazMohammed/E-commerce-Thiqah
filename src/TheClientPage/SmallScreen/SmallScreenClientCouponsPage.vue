<template>
  <div class="UserAdd">
    <v-app-bar flat class="mb-5 light-blue darken-1" app>
      <v-toolbar-title class="toolbar-title">
        <!-- <v-icon size="22">mdi-ticket-percent</v-icon> -->
        القسائم
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" color="white" icon>
        <v-icon size="30">mdi-arrow-left-thin</v-icon>
      </v-btn>
    </v-app-bar>
    <v-sheet height="56"></v-sheet>
    <v-container class="">
      <v-card-title class="coupons-recommended-title pa-0 px-1">
        قسائم موصى بها
      </v-card-title>
      <v-row no-gutters>
        <v-col class="pa-1" sm="6" cols="12" v-for="n in 3" :key="n">
          <v-sheet
            style="position: relative"
            rounded="lg"
            class="light-blue darken-1 pa-2 pt-0"
          >
            <!-- if store include in thiqah mall   -->
              
            <!-- Store Info  -->
            <v-row justify="center" align="center" no-gutters class="pa-2">
              <v-avatar class="profile" color="transparent" size="30">
                <v-img
                  src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                ></v-img>
              </v-avatar>
              <span class="store-name mr-1"> متجر بهلول </span>
              <v-spacer></v-spacer>
              <span class="coupons-date"> 
              ثـقـة مول  
              </span>
            </v-row>
            <v-card flat color="#fff">
              <v-row no-gutters justify="center" class="main">
                <v-col style="border-left: 2px dashed #eee" class="" cols="3">
                  <v-row
                    align="center"
                    style="height: 100%"
                    justify="center"
                    no-gutters
                  >
                    <v-avatar
                      tile
                      class="profile my-auto"
                      color="transparent"
                      size="70"
                    >
                      <v-img
                        src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                      ></v-img>
                    </v-avatar>
                  </v-row>
                </v-col>
                <v-col class="pa-1" cols="6">
                  <v-card-subtitle class="text pa-0">
                    خصم <span class="mx-1 red--text"><span>20</span>%</span>
                  </v-card-subtitle>
                  <v-card-text class="pa-0 text">
                    أنفق
                    <span class="mx-1">
                      52<v-icon left size="17">mdi-currency-rial</v-icon>
                    </span>
                    كحد أدنى
                  </v-card-text>
                  <v-card-text class="pa-0 text">
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
                    <v-btn
                      small
                      fab
                      dark
                      class="light-blue darken-1 btn"
                      elevation="0"
                    >
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
                <li></li>
              </ul>
            </v-card>
          </v-sheet>
        </v-col>
      </v-row>

      <v-divider class="my-2"></v-divider>
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
  .coupons-recommended-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0px;
    color: $fontcolor !important;
    font-size: 16px !important;
  }
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0.5px;
    color: $fontcolorsm !important;
    font-size: 15px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: #01579b !important;
      margin-left: 5px;
    }
  }

  .store-name {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0px;
    font-size: 15px !important;
    color: $fontcolorsm !important;
    // font-weight: 600 !important;
    pointer-events: none;
  }
  .coupons-date {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0px;
    padding: 3px 4px;
    font-size: 12px !important;
    color: $fontcolorsm !important;
    background-color: #FF3D00;
    font-weight: 600 !important;
    pointer-events: none;
    border-radius: 5px;
  }
}
.text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  font-weight: 600 !important;
  font-size: 12px !important;
}
.btn {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolorsm !important;
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
  z-index: 2;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  li {
    list-style: none;
    width: 6px;
    height: 6px;
    border-top: 1px solid transparent;
    border-right: 1px solid transparent;
    background-color: #039be5;
    transform: rotate(45deg);
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
