<template>
  <div class="Share">
    <v-app-bar flat color="deep-purple lighten-1" class="mb-5" app>
      <v-toolbar-title class="toolbar-title"> شارك وأربح </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon color="deep-purple lighten-4" size="30">
          mdi-arrow-left-thin
        </v-icon>
      </v-btn>
    </v-app-bar>
    <v-container style="margin-top: 56px" class="container py-0">
      <!-- <v-row no-gutters justify="center">
        <v-avatar size="50" color="#fc624d">
          <v-icon color="white" large>mdi-balloon</v-icon>
        </v-avatar>
      </v-row> -->
      <!-- <div class="py-3 d-flex font-weight-bold tital">
        شارك وأحصل على 26 نقطة عند دعوة أشخاص أخرين
      </div> -->
      <v-timeline dense>
        <v-timeline-item color="deep-purple " small>
          <v-card color="deep-purple lighten-1 " class="elevation-2">
            <v-card-text class="share-text">
              قم بدعوة أشخاص بتسجيل على موقعنا عن طريق الرابط الخاص بك
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="deep-purple " small>
          <v-card color="deep-purple lighten-1 " class="elevation-2">
            <v-card-text class="share-text">
              سوف تحصل على نقاطك عندما يتم التسجيل من قبل المستخدم بشكل كامل
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="deep-purple " small>
          <v-card color="deep-purple lighten-1 " class="elevation-2">
            <v-card-text class="share-text">
              قم بتحويل النقاط الى أموال أو بإمكانك الشراء من خلال الموقع
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="deep-purple " small>
          <v-card
            style="height: calc(100vh - 405px)"
            color="deep-purple lighten-1 "
            class="elevation-2 pa-2"
          >
            <v-row
              align="center"
              no-gutters
              style="height: 100%; flex-direction: column"
            >
              <span class="link-text">رابطك الخاص هو : </span>
              <v-spacer></v-spacer>
              <v-card-text class="link text-center">
                https://app.netlify.com/teams/mumtazmohammed/overview
              </v-card-text>
              <v-spacer></v-spacer>

              <v-btn text class="link-copy">نــسـخ</v-btn>
            </v-row>
          </v-card>
        </v-timeline-item>
      </v-timeline>
      <!-- <v-row>
        <v-col cols="12" class="pt-">
          <v-timeline>
            <v-timeline-item>
              قم بدعوة أشخاص بتسجيل على موقعنا عن طريق الرابط الخاص بك
            </v-timeline-item>
            <v-timeline-item class="text-right">
              سوف تحصل على نقاطك عندما يتم التسجيل من قبل المستخدم بشكل كامل
            </v-timeline-item>
            <v-timeline-item>
              قم بتحويل النقاط الى أموال أو بإمكانك الشراء من خلال الموقع
            </v-timeline-item>
          </v-timeline>
          <v-card class="mb-2 overflow-hidden" width="100%">
            <div>
              <span class="span-no">1</span>
            </div>
            <v-card-text class="how-to-use">
              قم بدعوة أشخاص بتسجيل على موقعنا عن طريق الرابط الخاص بك
            </v-card-text>
          </v-card>
          <v-card class="mb-2 overflow-hidden" width="100%">
            <div>
              <span class="span-no">2</span>
            </div>
            <v-card-text class="how-to-use">
              سوف تحصل على نقاطك عندما يتم التسجيل من قبل المستخدم بشكل كامل
            </v-card-text>
          </v-card>
          <v-card class="overflow-hidden" width="100%">
            <div>
              <span class="span-no">3</span>
            </div>
            <v-card-text class="how-to-use">
              قم بتحويل النقاط الى أموال أو بإمكانك الشراء من خلال الموقع
            </v-card-text>
          </v-card>
        </v-col>
        <v-col class="pa-2" cols="12">
          <v-card style="overflow: hidden" outlined>
            <v-card-actions class="align-center pa-0">
              <v-text-field
                hide-details
                dense
                readonly
                solo
                flat
                class="rounded-0"
                v-model="link"
              ></v-text-field>
              <v-btn elevation="0" height="38" tile class="copy-btn">
                نسخ
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row> -->
    </v-container>
  </div>
</template>

<script>
export default {
  name: "BestOffer",
  components: {},
  data() {
    return {
      link: "http://localhost:8081/SmallScreenShare/%D8%B4%D8%A7%D8%B1%D9%83%2F&%20%D9%88%D8%A3%D8%AD%D8%B5%D9%84%20%D8%B9%D9%84%D9%89%2026%20%D9%86%D9%82%D8%B7%D8%A9",
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetCarVerified = [];
      for (let i = 0; i < this.VerifiedCar.length; i++) {
        if (this.VerifiedCar[i].Vip == true) {
          GetCarVerified.push(this.VerifiedCar[i]);
        }
      }
      return GetCarVerified;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Share {
  width: 100%;
  height: 100vh;
  background-color: #d1c4e9;
  overflow: hidden;
  .toolbar-title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorsm !important;
    font-size: 15px !important;
    font-weight: 600;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    .v-icon {
      color: $fontcolorsm !important;
      margin-left: 5px;
    }
  }
  .share-text {
    font-family: $fontfamliy3 !important;
    font-size: 14px !important;
    color: $fontcolorsm !important;
    letter-spacing: 0px !important;
  }
}
.link {
  font-family: sans-serif !important;
  font-size: 17px !important;
  color: $fontcolorsm !important;
  letter-spacing: 0px !important;
}
.link-text {
  font-family: $fontfamliy3 !important;
  font-size: 17px !important;
  color: $fontcolorsm !important;
  letter-spacing: 0px !important;
}
.link-copy {
  font-family: $fontfamliy3 !important;
  font-size: 17px !important;
  color: $fontcolorsm !important;
  letter-spacing: 0px !important;
}
</style>
