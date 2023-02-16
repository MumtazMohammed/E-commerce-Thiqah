<template>
  <div class="BestOffer my-2">
    <v-container class="container py-0">
      <v-card tile color="transparent" flat class="card-wrapping">
        <div class="pa-2 align-center d-flex font-weight-bold tital">
          عروضات
          <strong class="mx-1">مجنونه</strong>
          <v-icon right color="#fc624d">mdi-flash</v-icon>
          <!-- بأفضل
          <strong class="mx-1">الأسعار</strong> -->
          <v-spacer></v-spacer>
          <countdown :time="2 * 24 * 60 * 60 * 1000">
            <template slot-scope="props">
              <v-row
                align="center"
                no-gutters
                style="flex-direction: row-reverse"
              >
                <span class="Countdown">
                  {{ props.days }}
                </span>
                <span class="Countdown">
                  {{ props.hours }}
                </span>
                <span class="Countdown">
                  {{ props.minutes }}
                </span>
                <span class="Countdown">
                  {{ props.seconds }}
                </span>
              </v-row>
            </template>
          </countdown>
        </div>
        <swiper class="swiper" :options="swiperOption">
          <swiper-slide v-for="(Product, index) in getCarInfo" :key="index">
            <div style="position: relative">
              <h1 class="ribbon">متميز</h1>
              <v-card
                :to="{
                  name: 'ShowTheProduct',
                  params: {
                    carName: Product.name,
                    carShape: Product.Shape,
                    carId: Product.id,
                    Company: Product.folder,
                  },
                }"
                width="100%"
                height="240"
                class=""
                rounded="md"
                outlined
                style="overflow: hidden; background-color: #eee"
              >
                <div v-if="Product.discountPercent" class="best-price-tag">
                  <small class="discountPercent">
                    {{ Product.discountPercent }}-
                  </small>
                </div>
                <v-img
                  height="130"
                  :src="getimageUrl(Product.folder, Product.image)"
                ></v-img>
                <v-row no-gutters>
                  <v-card-text
                    class="d-block card-text py-1 pa-2 text-truncate"
                  >
                    {{ Product.name }} {{ Product.company }}
                  </v-card-text>
                </v-row>
                <v-card-actions class="py-1 justify-center">
                  <strong class="PriceAfter text-truncate">
                    {{ Product.payment }}
                    <small class="text-truncate">ريال</small>
                  </strong>
                </v-card-actions>

                <v-card-text class="progress-info pa-0">
                  المتبقي
                  <span class="mr-1">14</span>
                </v-card-text>
                <div style="position: relative">
                  <v-icon class="v-icon-most-sel">mdi-fire</v-icon>
                  <v-sheet
                    style="position: relative; overflow: hidden"
                    class="my-2 mx-auto text-center"
                    width="80%"
                    color="#ffab91"
                    rounded="lg"
                    height="10"
                  >
                    <span class="progress"></span>
                  </v-sheet>
                </div>
              </v-card>
            </div>
          </swiper-slide>
          <swiper-slide>
            <v-card
              flat
              max-width="190px"
              height="240px"
              router
              color="transparent"
              class="overflow-hidden d-flex flex-column justify-center align-center"
            >
              <v-card-text class="text-center py-1 card-text-seeMore">
                الكل
              </v-card-text>
              <v-icon size="17" class="deep-orange--text text--darken-1">
                mdi-plus</v-icon
              >
            </v-card>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "BestOffer",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      VerifiedCar,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 10,
        autoplay: false,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,
          type: "progressbar",
        },

        breakpoints: {
          1024: {
            slidesPerView: 6,
            slidesPerGroup: 6,
          },
          768: {
            slidesPerView: 5,
            slidesPerGroup: 5,
          },
          640: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          471: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          470: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          250: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
        },
      },
    };
  },
  // this is help full to call the image inside folder and inject to the src
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
.BestOffer {
  width: 100%;
  min-height: 20vh;
  background-color: #eeeee4;

  .swiper {
    height: 270px;
    // padding-bottom: 45px;
    padding-right: 5px !important;
    padding-left: 3px;
    .swiper-slide {
      height: 240px !important;
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
    background-color: #fff;

    span.swiper-pagination-progressbar-fill {
      background-color: $color-2;
    }
  }
  .v-sheet {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }

  .container {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }
  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 15px !important;
    color: $fontcolor;
  }
  .tital {
    font-family: $fontfamliy3;
    font-size: 22px;
    color: $color-2;
    letter-spacing: 0px !important;
    pointer-events: none;
    @media (max-width: 470px) {
      font-size: 18px;
    }
    @media (max-width: 350px) {
      font-size: 17px;
    }
  }
  a {
    font-size: 13px;
  }
}

::v-deep i.v-icon.notranslate.material-icons.theme--light {
  color: $color-2;
  font-size: 28px;
  font-weight: 600;
}

.card-text-seeMore {
  font-family: $fontfamliy3;
  letter-spacing: 0;
  font-size: 16px;
  color: $fontcolorlinks !important;
}
// Products
.sold-info {
  font-family: $fontfamliy3 !important;
  font-size: 12px !important;
  font-weight: 600 !important;
  color: $fontcolorlinks;
  span {
    color: $color-2 !important;
    margin-left: 5px;
    font-size: 14px !important;
    letter-spacing: 1.5px !important;
  }
}
.PriceAfter {
  font-size: 18px !important;
  display: block !important;
  color: $color-2;
  font-weight: 700 !important;
  font-family: sans-serif !important;
}
.best-price-tag {
  position: absolute;
  left: 4px;
  top: 0px;
  clip-path: polygon(
    50% 0%,
    100% 0,
    100% 35%,
    100% 70%,
    100% 100%,
    49% 70%,
    0 100%,
    0% 70%,
    0% 35%,
    0 0
  );

  background-color: $color-2;
  width: 35px;
  height: 40px;
  display: flex;
  justify-content: center;
  // transform: rotate(360deg);
  z-index: 1;
  border-radius: 0 !important;
}
.discountPercent {
  color: white !important;
  font-weight: 500;
  font-size: 13px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
}
//
.ribbon {
  position: absolute;
  top: 3px;
  right: 0;
  z-index: 1;
  width: 50px;
  text-align: center;
  font-size: 11px;
  color: #ffffff;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  border-radius: 5px 0px 0px 5px !important;
  background: $color-2;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
}

.ribbon:before,
.ribbon:after {
  position: absolute;
  content: "";
  display: block;
}

.ribbon:before {
  width: 0.469em;
  height: 100%;
  padding: 0 0 0.438em;
  top: 0;
  right: -0.469em;
  background: inherit;
  border-radius: 0px 5px 5px 0px !important;
}

.ribbon:after {
  width: 0.313em;
  height: 0.313em;
  background: rgba(0, 0, 0, 0.35);
  bottom: -0.313em;
  right: -0.314em;
  border-radius: 0px 5px 5px 0px !important;
  box-shadow: inset -1px 2px 2px rgba(0, 0, 0, 0.3);
}
.progress {
  position: absolute;
  left: 0;
  top: 0;
  width: 70%;
  height: 100%;
  background-color: $color-2;
  // border-radius: 1000px !important;
}
.progress-info {
  // color: ;
  text-align: center;
  letter-spacing: 0 !important;
  font-size: 14px !important;
  color: #2f2f2f;
  font-weight: 600;
  font-family: $fontfamliy3 !important;
  z-index: 2;
}
.v-icon-most-sel {
  position: absolute !important;
  top: -9px;
  right: 11px;
  font-size: 22px !important;
  color: #ffca28 !important;
  z-index: 10;
}
.Countdown {
  width: 27px !important;
  // height: 20px !important;
  // display: block !important;
  background-color: $color-2 !important;
  color: #eee !important;
  margin: 0 3px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3px 0 !important;
  border-radius: 5px;
  font-family: sans-serif !important;
  font-size: 18px !important;
  @media (max-width: 600px) {
    font-size: 15px !important;
  }
}
</style>
