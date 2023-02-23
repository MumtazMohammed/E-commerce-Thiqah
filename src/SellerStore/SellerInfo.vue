<template>
  <v-card rounded="lg" class="AboutStore overflow-hidden">
    <v-row no-gutters>
      <v-avatar tile size="140">
        <v-img
          src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
        ></v-img>
      </v-avatar>
      <v-col cols="">
        <v-list-item two-line>
          <v-list-item-content class="py-0">
            <v-list-item-title class="store-name mb-2">
              محمد أمين الحريبي
            </v-list-item-title>
            <v-list-item-subtitle>
              <v-card class="overflow-hidden" flat rounded="sm" max-width="170">
                <v-row align="center" class="fill-height" no-gutters>
                  <span class="store-with-thiah white--text red">
                    ثقة مول
                  </span>
                  <v-icon color="red" class="mx-1">mdi-check-decagram</v-icon>
                  <span class="store-with-thiah black--text">بائع مرخص</span>
                </v-row>
              </v-card>
            </v-list-item-subtitle>
            <v-card-actions class="justify-center">
              <v-btn min-width="80px" dark class="red btn" rounded="pll"
                >متابعة</v-btn
              >
              <v-btn min-width="80px" class="btn" rounded="pll">مراسلة</v-btn>
            </v-card-actions>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col class="hidden-sm-and-down" cols="3">
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col class="hidden-sm-and-down" cols="3">
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item two-line>
          <v-list-item-content class="py-1">
            <v-list-item-title>Two-line item</v-list-item-title>
            <v-list-item-subtitle>Secondary text</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      colors: [
        "indigo",
        "warning",
        "pink darken-2",
        "red lighten-1",
        "deep-purple accent-4",
      ],
      slides: ["First", "Second", "Third", "Fourth", "Fifth"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  // computed: {
  //   getCarInfo() {
  //     let GetShowroomfeatured = [];
  //     for (let i = 0; i < this.featuredshowrooms.length; i++) {
  //       if (this.featuredshowrooms[i].featured == true) {
  //         GetShowroomfeatured.push(this.featuredshowrooms[i]);
  //       }
  //     }
  //     return GetShowroomfeatured;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.AboutStore {
  background: rgba(255, 255, 255, 0.2) !important;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1) !important;
  backdrop-filter: blur(5px) !important;
  -webkit-backdrop-filter: blur(5px);
}
.store-name {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  color: #fff !important;
  font-size: 18px;
}
.btn {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-weight: 600;
}
.store-with-thiah {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  padding: 5px;
}
::v-deep .v-avatar.rounded-0 {
  @media (max-width: 600px) {
    height: 120px !important;
    min-width: 120px !important;
    width: 120px !important;
  }
}
::v-deep .v-list-item.v-list-item--two-line {
  min-height: 40px !important;
}
</style>
