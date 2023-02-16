<template>
  <div class="Shape_box">
    <v-container class="py-2 pb-1 px-2 px-md-1 px-lg-1 px-sm-1">
      <!-- <v-card class="mx-auto" style="margin-top: -20px; z-index: 8" height="30" width="80%">
      </v-card> -->
      <v-card flat color="#f8f9fa" class="pa-1">
        <swiper class="swiperR" :options="swiperOption">
          <swiper-slide>
            <v-card class="my-2 mb-3" color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="green darken-1 pa-1"
                >
                  mdi-taxi
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> توصيل </v-card-text>
            </v-card>
            <v-card color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="green accent-4 pa-1"
                >
                  mdi-cart-variant
                </v-icon>
                <v-card-text class="text mt-2 pa-0"> سوبر ماركت </v-card-text>
              </v-row>
            </v-card>
          </swiper-slide>
          <swiper-slide>
            <v-card class="my-2 mb-3" color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="deep-purple lighten-1 pa-1"
                >
                  mdi-car
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> معرض السيارات </v-card-text>
            </v-card>
            <v-card color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="yellow darken-4 pa-1"
                >
                  mdi-food
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> المطاعم </v-card-text>
            </v-card>
          </swiper-slide>
          <swiper-slide>
            <v-card class="my-2 mb-3" color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="indigo lighten-1 pa-1"
                >
                  mdi-home-silo
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> العقارات </v-card-text>
            </v-card>
            <v-card color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="pink darken-1 pa-1"
                >
                  mdi-shopping
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> ثقة مول </v-card-text>
            </v-card>
          </swiper-slide>
          <swiper-slide>
            <v-card class="my-2 mb-3" color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="blue darken-1 pa-1"
                >
                  mdi-earth
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> السفريات </v-card-text>
            </v-card>
            <v-card color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="blue-grey darken-2 pa-1"
                >
                  mdi-cellphone-message
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0">فواتير & رصيد </v-card-text>
            </v-card>
          </swiper-slide>
          <swiper-slide>
            <v-card class="my-2 mb-3" color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="brown lighten-1 pa-1"
                >
                  mdi-cog-transfer
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0"> خدمات هندسية </v-card-text>
            </v-card>
            <v-card color="transparent" elevation="0">
              <v-row no-gutters justify="center" align="center">
                <v-icon
                  style="border-radius: 5px"
                  size="30"
                  color="#eee"
                  class="teal accent-4 pa-1"
                >
                  mdi-code-greater-than-or-equal
                </v-icon>
              </v-row>
              <v-card-text class="text mt-2 pa-0">خدمات برمجية </v-card-text>
            </v-card>
          </swiper-slide>
          <div
            class="swiper-pagination swiper-pagination-bullets"
            slot="pagination"
          ></div>
        </swiper>
      </v-card>

      <v-img
        class=""
        max-height="300"
        src="https://cf.shopee.com.my/file/my-50009109-69f0041a5f226fe98cb3e5ac3eea4474_xxhdpi"
      >
      </v-img>
    </v-container>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
export default {
  name: "CarShape",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      items: [
        {
          color: "red lighten-2",
          icon: "mdi-star",
        },
        {
          color: "purple darken-1",
          icon: "mdi-book-variant",
        },
        {
          color: "green lighten-1",
          icon: "mdi-airballoon",
        },
        {
          color: "indigo",
          icon: "mdi-buffer",
        },
      ],

      Services: [
        {
          ServicId: 1,
          ServicText: "خدمة هندسية ",
          ServicIcon: "mdi-drawing-box",
          ServicColor: "red--text text--darken-1",
          Color: "red",
        },
        {
          ServicId: 2,
          ServicText: "خدمة برمجية",
          ServicIcon: "mdi-code-greater-than-or-equal",
          ServicColor: "blue--text text--darken-2",
        },
        {
          ServicId: 3,
          ServicText: " نتكفلك في البيع",
          ServicIcon: "mdi-file-sign",
          ServicColor: "",
        },

        {
          ServicId: 6,
          ServicText: "السفريات",
          ServicIcon: "mdi-earth",
          ServicColor: "deep-orange--text",
        },
      ],

      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "card",
        // spaceBetween: 6,
        autoplay: false,
        loop: false,
        slidesPerView: 4,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,
          type: "progressbar",
        },
      },
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

.Shape_box {
  background-color: #f8f9fa;
}
.text {
  font-family: $fontfamliy3 !important;
  font-size: 14px !important;
  letter-spacing: 0 !important;
  color: $fontcolor !important;
  font-weight: 600;
  text-align: center;
  @media (max-width: 600px) {
    font-size: 13px !important;
  }
}

.swiperR {
  height: 182px;

  .swiper-slide {
    height: 152px;
  }
}
::v-deep .swiper-container-horizontal > .swiper-pagination-progressbar {
  top: 95% !important;
  width: 50px;
  height: 5px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 10px;
  overflow: hidden;
  background-color: #eee;

  span.swiper-pagination-progressbar-fill {
    background-color: $color-2;
  }
}
</style>
