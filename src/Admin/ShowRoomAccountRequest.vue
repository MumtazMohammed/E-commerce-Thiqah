<template>
  <div class="ShowRoomAccountRequest">
    <v-container>
      <v-row>
        <v-col cols="12">
          <h2>الطلبات لفتح المعرض</h2>
        </v-col>
        <v-col cols="12" md="6" sm="12">
          <v-card-actions class="pa-1 px-2 justify-center align-center">
            <v-btn small dark icon elevation="0" class="green">
              <v-icon>mdi-check</v-icon>
            </v-btn>
            <v-btn small dark icon elevation="0" class="red">
              <v-icon>mdi-close</v-icon>
            </v-btn>
            <v-card
              flat
              color="grey darken-3"
              dark
              class="rounded-pill mx-auto"
              width="300"
            >
              <v-card-title class="pa-0 justify-center">
                M0124741
              </v-card-title>
            </v-card>
          </v-card-actions>
          <v-card tile outlined class="py-2">
            <v-card-title class="justify-center py-2 text">
              فتح المعرض من قبل :
              <v-card-title class="pa-0 pr-2 text blue--text">
                وكيل
              </v-card-title>
            </v-card-title>
            <v-card-title class="justify-center py-2 text">
              أسم صاحب الطلب :
              <v-card-title class="pa-0 pr-2 text blue--text">
                محمد أمين شمسان
              </v-card-title>
            </v-card-title>
            <v-card-title class="justify-center py-2 text">
              البريد الأكترواني :
              <v-card-title class="pa-0 pr-2 text blue--text">
                ksmc45@gmail.com
              </v-card-title>
            </v-card-title>
            <v-card-title class="justify-center py-2 text">
              رقم الهاتف :
              <v-card-title class="pa-0 pr-2 text blue--text">
                01121331731
              </v-card-title>
            </v-card-title>
            <v-card-title class="justify-center py-2 text">
              رقم الوتس آب :
              <v-card-title class="pa-0 pr-2 text blue--text">
                01121331731
              </v-card-title>
            </v-card-title>
            <v-card-title class="justify-center py-2 text">
              كلمة المرور :
              <v-card-title class="pa-0 pr-2 text blue--text">
                01121331731
              </v-card-title>
            </v-card-title>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "ShowRoomAccountRequest",
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
.ShowRoomAccountRequest {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
  // padding: $padding;
  font-family: $fontfamliy !important;
  letter-spacing: 0px;
  h2 {
    font-family: $fontfamliy !important;
    letter-spacing: 0px;
    color: $fontcolor;
  }
  .text {
    font-size: 17px !important;
  }
}
</style>
