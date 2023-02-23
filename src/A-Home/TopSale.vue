<template>
  <div class="BestOffer py-2">
    <v-container class="container py-0">
      <div class="pa-2 tital">الأعلى مبيعاً</div>
      <swiper class="swiper" :options="swiperOption">
        <swiper-slide v-for="(Product, index) in VerifiedCar" :key="index">
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
            height="195"
            flat
            style="overflow: hidden; position: relative"
          >
            <v-img
              max-height="100"
              style="overflow: hidden"
              :src="getimageUrl(Product.folder, Product.image)"
            >
              <span v-if="index == 0" class="top grey lighten-4">
                <v-icon color="#ffd700">mdi-seal</v-icon>

                {{ index + 1 }}
              </span>
              <span v-if="index == 1" class="top grey lighten-4">
                <v-icon color="#c0c0c0">mdi-seal</v-icon>

                {{ index + 1 }}
              </span>
              <span v-if="index == 2" class="top grey lighten-4">
                <v-icon color="#cd7f32">mdi-seal</v-icon>
                {{ index + 1 }}
              </span>
              <span v-else-if="index >= 3" class="top grey lighten-4">
                <v-icon color="#00BCD4">mdi-seal</v-icon>
                {{ index + 1 }}
              </span>
            </v-img>
            <v-card flat tile color="#eee">
              <span class="d-block card-text pa-1 text-truncate">
                {{ Product.name }} {{ Product.company }} {{ Product.name }}
              </span>
            </v-card>
            <v-row
              style="min-height: 20px"
              no-gutters
              align="end"
              justify="center"
              class=""
            >
              <strong class="PriceAfter text-truncate">
                {{ Product.payment }}
                <small class="text-truncate">ريال</small>
              </strong>
            </v-row>
            <v-row
              style="min-height: 30px"
              no-gutters
              align="end"
              justify="center"
            >
              <span class="sold-text px-3 text-truncate">
                عدد المشترين : <span>{{ index + 70 }}</span>
              </span>
            </v-row>
          </v-card>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
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
      chip: 0,
      VerifiedCar,
      carName: this.$route.params.carName,
      carId: this.$route.params.carId,
      CarShape: this.$route.params.CarShape,
      Company: this.$route.params.Company,
      swiperOption: {
        freeMode: false,
        effect: "cards",
        spaceBetween: 8,
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
            slidesPerView: 2,
            slidesPerGroup: 2,
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
  // display: flex;
  justify-content: center;
  // align-items: center;
  background-color: $color-background;
  // font-family: $fontfamliy;
  .container {
    @media (max-width: 950px) {
      padding-left: 0px !important;
      padding-right: 0px !important;
    }
  }
  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    color: $fontcolorlinks;
    // background-color: aqua;
    span {
      font-size: 15px;
      font-weight: 600;
      color: $fontcolor;
      letter-spacing: 2px;
    }
  }
  .sold-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 14px;
    color: $fontcolorlinks;
    background-color: #eee;
    border-radius: 30px !important;
    span {
      font-family: sans-serif !important;
      font-size: 17px;
      font-weight: 700;
      color: $fontcolor;
    }
  }
  .PriceAfter {
    font-size: 18px !important;
    display: block !important;
    color: $color-2;
    font-weight: 700 !important;
    font-family: sans-serif !important;
  }
  .tital {
    font-family: $fontfamliy3;
    font-size: 22px;
    color: #ff5722;
    letter-spacing: 0px !important;
    pointer-events: none;
    // text-align: center;
    font-weight: 600;
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

//
.swiper {
  height: 230px;

  margin-left: auto;
  margin-right: auto;

  .swiper-slide {
    height: 195px;
    // margin: 1px !important;
    // margin-bottom: 5px !important;
  }
}
::v-deep .swiper-container-horizontal > .swiper-pagination-progressbar {
  top: 95% !important;
  width: 50px;
  height: 5px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 5px;
  overflow: hidden;
  background-color: #eee;

  span.swiper-pagination-progressbar-fill {
    background-color: $color-2;
    box-shadow: inset 0 0 0 0.2px #eee;
  }
}
::v-deep.swiper-container {
  padding-right: 5px;
  padding-left: 5px !important;
}
::v-deep .v-slide-group__content {
  justify-content: end;
}

.top {
  // clip-path: polygon(0 0, 100% 0%, 100% 70%, 50% 100%, 0 70%);
  // background-color: aqua;
  width: 40px;
  height: 50px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding-top: 2px;
  font-size: 15px;
  margin-right: 5px;
  font-weight: 600;
  color: #757575 !important;
}
</style>
