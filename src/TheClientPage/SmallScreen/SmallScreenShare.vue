<template>
  <div class="Share">
    <v-app-bar flat color="#fc624d" class="mb-5" app>
      <v-toolbar-title class="toolbar-title"> شارك وأربح </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn to="/TheUserPageView" icon>
        <v-icon color="deep-purple lighten-4" size="30">
          mdi-arrow-left-thin
        </v-icon>
      </v-btn>
    </v-app-bar>
    <v-container style="margin-top: 56px" class="container py-0 pr-0">
      <v-timeline dense>
        <v-timeline-item color="#fc624d" small>
          <v-card class="elevation-0" color="white">
            <v-card-text class="share-text">
              قم بدعوة أشخاص بتسجيل على موقعنا عن طريق الرابط الخاص بك
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="#fc624d" small>
          <v-card color="white" class="elevation-0">
            <v-card-text class="share-text">
              سوف تحصل على نقاطك عندما يتم التسجيل من قبل المستخدم بشكل كامل
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="#fc624d " small>
          <v-card class="elevation-0" color="white">
            <v-card-text class="share-text">
              قم بتحويل النقاط الى أموال أو بإمكانك الشراء من خلال الموقع
            </v-card-text>
          </v-card>
        </v-timeline-item>
        <v-timeline-item color="#fc624d" small>
          <v-card
            style="height: calc(100vh - 450px)"
            class="elevation-0 pa-2"
            color="white"
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

              <v-btn block text class="link-copy">نــسـخ</v-btn>
            </v-row>
          </v-card>
        </v-timeline-item>
      </v-timeline>
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
  background-color: #fbe9e7;
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
    font-size: 15px !important;
    color: $fontcolor !important;
    letter-spacing: 0px !important;
  }
}
.link {
  font-family: sans-serif !important;
  font-size: 17px !important;
  color: $fontcolorlinks !important;
  letter-spacing: 0px !important;
}
.link-text {
  font-family: $fontfamliy3 !important;
  font-size: 17px !important;
  color: $fontcolor !important;
  letter-spacing: 0px !important;
}
.link-copy {
  font-family: $fontfamliy3 !important;
  font-size: 17px !important;
  color: $fontcolor !important;
  letter-spacing: 0px !important;
}
</style>
