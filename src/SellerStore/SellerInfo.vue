<template>
  <v-card  tile color="#6A76AB" rounded="md" class="AboutStore overflow-hidden">
    <v-container class="px-1 pb-1">
      <v-row no-gutters align="center">
        <v-avatar size="80">
          <v-img
            src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
          ></v-img>
        </v-avatar>
        <v-col cols="6">
          <v-list-item two-line class="pt-2 pr-1 pa-0">
            <v-list-item-content class="pa-0">
              <v-list-item-title class="store-name mb-2">
                محمد أمين الحريبي محمد أمين الحريبي
              </v-list-item-title>
              <v-list-item-subtitle>
                <v-card
                  class="overflow-hidden"
                  flat
                  rounded="sm"
                  max-width="160"
                >
                  <v-row align="center" class="fill-height" no-gutters>
                    <span class="store-with-thiah white--text red">
                      ثقة مول
                    </span>
                    <v-icon size="22" color="red" class=""
                      >mdi-check-decagram</v-icon
                    >
                    <span class="store-with-thiah black--text">بائع مرخص</span>
                  </v-row>
                </v-card>
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-card-title class="py-1">
            <v-icon size="20">mdi-account</v-icon>
            <span>5</span>
            <v-icon size="20">mdi-star</v-icon>
            <span>5</span>
          </v-card-title>
        </v-col>
        <v-spacer></v-spacer>
        <v-col cols="3">
          <v-row
            style="flex-direction: column"
            align="center"
            justify="center"
            no-gutters
            class="fill-height pa-1"
          >
            <v-btn width="35" height="28" depressed dark class="red ma-1 btn">
              متابعة
            </v-btn>
            <v-btn width="35" height="28" depressed class="btn"> مراسلة </v-btn>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
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
  font-size: 14px !important ;
}
.store-with-thiah {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  padding: 5px;
  font-size: 13px;
  @media (max-width: 400px) {
  }
}
::v-deep .v-avatar {
  @media (max-width: 600px) {
    height: 80px !important;
    min-width: 80px !important;
    width: 80px !important;
  }
}
::v-deep .v-list-item.v-list-item--two-line {
  min-height: 40px !important;
}
</style>
