<template>
  <div class="AboutStore">
    <v-card-title class="pa-2 titel"> عن المتجر </v-card-title>
    <v-row no-gutters>
      <v-col cols="12">
        <v-card-text class="text py-2">
          حيث يحتاج العميل فى كثير من الأحيان أن يطلع على صورة حقيقية لتصميم
          الموقع. ومن هنا وجب على المصمم أن يضع نصوصا مؤقتة على التصميم ليظهر
          للعميل الشكل كاملاً،دور مولد النص العربى أن يوفر على المصمم عناء البحث
          عن نص بديل لا علاقة له بالموضوع الذى يتحدث عنه التصميم فيظهر بشكل لا
          يليق.
        </v-card-text>
      </v-col>
      <v-col cols="12">
        <v-sheet
          height="auto"
          min-height="200"
          class="overflow-hidden transparent"
        >
          <v-img
            contain
            max-height="300"
            src="https://picsum.photos/510/300?random"
          ></v-img>
        </v-sheet>
      </v-col>
    </v-row>
  </div>
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
  padding: 10px 0;
  background-color: $color-background !important;

  .titel {
    letter-spacing: 0 !important;
    font-size: 22px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
    justify-content: center;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    text-align: justify;
    line-height: 1.7;
  }
}
::v-deep
  button.v-carousel__controls__item.v-btn.v-item--active.v-btn--active.v-btn--icon.v-btn--round.theme--dark.v-size--small {
  width: 20px !important;
  height: 20px !important;
}
::v-deep .v-carousel__controls {
  height: 30px !important;
}
</style>
