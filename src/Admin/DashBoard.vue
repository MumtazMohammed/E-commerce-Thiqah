<template>
  <div class="DashBoard">
    <v-container>
      <v-card-title class="justify-center"> المعلومات </v-card-title>
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          v-for="(DashBord, i) in DashBords"
          :key="i"
          class="col-crad-info"
        >
          <v-card class="crad-info">
            <v-card-actions class="justify-center pa-1">
              <v-icon color="blue darken-2" v-text="DashBord.Icon"></v-icon>
            </v-card-actions>
            <v-card-title
              class="pa-2 DashBord-title justify-center"
              v-text="DashBord.Title"
            >
            </v-card-title>
            <v-card-actions class="justify-center pa-1">
              <span v-text="DashBord.Numbers"></span>
            </v-card-actions>
          </v-card>
          <!-- <v-card-actions class="SeeInfo justify-center">
            <v-btn text class="SeeInfo">
              <v-icon right>mdi-eye-circle-outline</v-icon>
              رؤية المعلومات
            </v-btn>
          </v-card-actions> -->
        </v-col>
      </v-row>
      <!-- Main Page Advertisement  -->
      <v-card-title class="justify-center"> الأعلانات </v-card-title>
      <v-row class="justify-center">
        <v-col cols="12">
          <v-carousel
            cycle
            hide-delimiters
            interval="3000"
            hide-delimiter-background
            class="carousel"
          >
            <v-carousel-item
              v-for="(slide, i) in slides"
              :key="i"
              style="height: 100%"
              class="carouselItem"
            >
              <v-img
                min-height="150"
                min-width="200"
                :src="slide.src"
                :lazy-src="slide.src"
              >
              </v-img>
            </v-carousel-item>
          </v-carousel>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      Users: "عدد المسجلين",
      Cars: "عدد السيارات",
      SeeInfo: "رؤية المعلومات",
      AdAadvertisement: "  إضافة صورة",
      files: [],
      DashBords: [
        {
          Title: "عدد المسجلين",
          Numbers: 421,
          Icon: "mdi-account-group",
        },
        {
          Title: " عدد المعارض قيد التشغيل",
          Numbers: 421,
          Icon: "mdi-store-check",
        },
        {
          Title: " عدد المعارض غير قيد التشغيل",
          Numbers: 421,
          Icon: "mdi-store-remove",
        },
        {
          Title: "عدد السيارات ",
          Numbers: 421,
          Icon: "mdi-car-3-plus",
        },
        {
          Title: "عدد السيارات المدفوعة",
          Numbers: 421,
          Icon: "mdi-credit-card-check",
        },
        {
          Title: "عدد السيارات لم يتم التحقق منها",
          Numbers: 421,
          Icon: "mdi-shield-alert",
        },
        {
          Title: "عدد السيارات  تم التحقق منها",
          Numbers: 421,
          Icon: "mdi-check-decagram",
        },
        {
          Title: "عدد الأشخاص المتاحين  في الموقع ",
          Numbers: 421,
          Icon: "mdi-tooltip-cellphone",
        },
      ],

      slides: [
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
        },
        {
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
        },
      ],
    };
  },
  methods: {
    onPickFile() {
      this.$refs.fileInput.click();
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.DashBoard {
  // padding: $padding;
  width: 100%;
  background-color: $color-background;
}
.Add-new-Ad {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-weight: 500px !important;
  // border: 2px solid grey;
  box-shadow: 0px 0px 1px 1px grey !important;
}
.v-card__title {
  font-family: $fontfamliy;
}
.DashBord-title {
  font-size: 15px !important;
}
.v-card__actions > .v-btn.v-btn {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-weight: 500;
  font-size: 17px;
}
// .col-crad-info {
//   position: relative;
// }
// .crad-info {
//   z-index: 1;
// }
// .col-crad-info:hover .crad-info {
//   transform: scale(0.9) translate(0%, -50%);
//   transition: all 0.5s ease;
//   overflow: hidden;
// }
// .SeeInfo {
//   position: absolute;
//   top: 80%;
//   left: 50%;
//   transform: translate(-50%, -80%);
//   .v-btn {
//     box-shadow: 0px 0px 1px 0px grey;
//   }
// }
::v-deep .v-window.v-item-group.theme--dark.v-carousel {
  height: 295px !important;
  @media (max-width: 700px) {
    height: 250px !important;
  }
  @media (max-width: 590px) {
    height: 210px !important;
  }
  @media (max-width: 520px) {
    height: 195px !important;
  }
}
::v-deep .v-image.v-responsive.theme--light {
  height: 295px !important;
  @media (max-width: 700px) {
    height: 250px !important;
  }
  @media (max-width: 590px) {
    height: 210px !important;
  }
  @media (max-width: 520px) {
    height: 195px !important;
  }
}
.carousel::v-deep .v-image.v-responsive.v-carousel__item.theme--light {
  // height: 100% !important;
  @media (max-width: 959px) {
    // background: $color-1;
  }
}
</style>
