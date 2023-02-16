<template>
  <div class="UserPageInfo">
    <v-container>
      <v-row>
        <v-col cols="12">
          <h2 class="header-title mb-3">صفحة المستخدم</h2>
          <v-card-actions>
            <!-- send message -->
            <div class="mx-1">
              <v-dialog v-model="dialog" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    v-bind="attrs"
                    v-on="on"
                    icon
                    elevation="2"
                    color="success"
                    class="white"
                  >
                    <v-icon>mdi-chat</v-icon>
                  </v-btn>
                </template>
                <v-card class="">
                  <v-card-actions>
                    <v-text-field
                      hide-details="true"
                      placeholder="عنوان الرسالة"
                    ></v-text-field>
                  </v-card-actions>
                  <v-card-actions>
                    <v-textarea
                      no-resize
                      rows="6"
                      class="pt-0 mt-0"
                      placeholder="الرسالة"
                      hide-details="true"
                    >
                    </v-textarea>
                  </v-card-actions>
                  <v-card-actions class="justify-center">
                    <v-btn class="send-btn">إرسال</v-btn>
                  </v-card-actions>
                  <v-divider></v-divider>
                  <v-card-actions>
                    <v-btn
                      class="send-btn"
                      color="primary"
                      outlined
                      @click="dialog = false"
                    >
                      إلغاء
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </div>
            <!-- delete the account -->
            <div class="mx-1">
              <v-btn icon elevation="2" color="red lighten-2" class="white">
                <v-icon>mdi-trash-can-outline</v-icon>
              </v-btn>
            </div>
          </v-card-actions>
          <v-divider></v-divider>
          <v-card class="mt-3" tile flat color="transparent">
            <v-card-actions class="justify-center">
              <v-img
                contain
                max-width="200"
                src="../assets/pp.jpg"
                alt="../assets/pp.jpg"
                style="border-radius: 10px"
              />
            </v-card-actions>
            <v-card-title class="text py-2"> الأسم : </v-card-title>
            <v-card-title class="text py-2"> البريد الأكتروني : </v-card-title>
            <v-card-title class="text py-2"> رقم الهاتف : </v-card-title>
            <v-card-title class="text py-2"> المدينة : </v-card-title>
            <v-card-title class="text py-2"> كلمة السر : </v-card-title>
          </v-card>
        </v-col>
        <!-- Cars Cards  -->
        <v-col cols="12" class="pb-0">
          <v-card outlined class="pa-3">
            <h3 class="header-title">السيارات المعلنة</h3>
          </v-card>
        </v-col>
        <v-col cols="12" md="4" sm="6" v-for="Car in Cars" :key="Car.id">
          <v-card
            :to="{
              name: 'UserCarDetails',
              params: {
                carId: Car.id,
              },
            }"
            outlined
            class="overflow-hidden"
          >
            <v-row>
              <v-col cols="3">
                <v-avatar tile size="70" color="grey darken-4">
                  <v-img
                    contain
                    :src="getimageUrl(Car.folder, Car.image)"
                    :lazy-src="getimageUrl(Car.folder, Car.image)"
                    :alt="getimageUrl(Car.folder, Car.image)"
                  />
                </v-avatar>
              </v-col>
              <v-col cols="9">
                <v-card-actions class="pa-0 justify-end">
                  <span class="dot-feature ma-1"></span>
                  <span class="dot-upgrade ma-1"></span>
                  <span class="dot-trusted ma-1"></span>
                </v-card-actions>

                <v-card-text class="text text-center py-1"
                  >{{ Car.id }}
                </v-card-text>
                <v-card-text class="text text-center py-1">
                  23 / 05 / 2022
                </v-card-text>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import Cars from "@/data-json/All-Car.json";
export default {
  name: "UserPAgeInfo",
  data() {
    return {
      Cars,
      carId: this.$route.params.CarType,
      dialog: false,
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
.UserPageInfo {
  width: 100%;
  min-height: 100vh;
  padding: $padding;
  background-color: $color-background;
  .text {
    font-family: $fontfamliy;
    letter-spacing: 0px;
    font-size: 17px !important;
  }
  .header-title {
    font-family: $fontfamliy;
    letter-spacing: 0px;
    text-align: center;
  }
  .dot-trusted {
    width: 7px;
    height: 7px;
    display: block;
    background-color: #1976d2;
    border-radius: 50%;
  }
  .dot-upgrade {
    width: 7px;
    height: 7px;
    display: block;
    background-color: #5e35b1;
    border-radius: 50%;
  }
  .dot-feature {
    width: 7px;
    height: 7px;
    display: block;
    background-color: #f57c00;
    border-radius: 50%;
  }
}
::v-deep.theme--light.v-input input::placeholder {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
::v-deep.theme--light.v-input textarea::placeholder {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
.send-btn {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-weight: bold;
}
</style>
