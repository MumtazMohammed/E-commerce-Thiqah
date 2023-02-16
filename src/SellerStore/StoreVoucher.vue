<template>
  <div class="StoreVoucher" style="overflow: hidden">
    <v-card-title class="titel justify-center pa-2">
      قسائم المتجر
    </v-card-title>
    <v-row no-gutters>
      <v-col
        class="pa-4 py-1"
        md="4"
        lg="4"
        sm="6"
        cols="12"
        v-for="n in 3"
        :key="n"
      >
        <v-card flat color="#eee" class="card">
          <v-row no-gutters justify="center" class="main">
            <v-col style="border-left: 1px dashed grey" class="" cols="3">
              <v-row
                align="center"
                style="height: 100%"
                justify="center"
                no-gutters
              >
                <v-avatar class="profile my-auto" color="grey" size="50">
                  <v-img
                    src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                  ></v-img>
                </v-avatar>
              </v-row>
            </v-col>

            <v-col class="pr-1" cols="6">
              <v-card-subtitle class="text pa-1">
                خصم <span class="mx-1 red--text"><span>20</span>%</span>
              </v-card-subtitle>
              <v-card-text class="pa-1 text">
                أنفق
                <span class="mx-1">
                  52<v-icon left size="17">mdi-currency-rial</v-icon>
                </span>
                كحد أدنى
              </v-card-text>
              <v-card-text class="pa-1 text">
                متاح حتى
                <span>10/2/2020</span>
              </v-card-text>
            </v-col>
            <v-col cols="3">
              <v-row
                align="center"
                style="height: 100%"
                justify="center"
                no-gutters
              >
                <v-btn small fab class="btn" elevation="0"> أخذ </v-btn>
              </v-row>
            </v-col>
          </v-row>
          <!-- <div class="copy-button">
        <input id="copyvalue" type="text" readonly value="GOFREE" />
        <button onclick="copyIt()" class="copybtn">COPY</button>
      </div> -->
          <ul class="Voucher">
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
          </ul>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import Services from "../data-json/showroom.json";
export default {
  name: "ServicesPage",
  components: {},
  data() {
    return {
      current: null,
      Services,
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 0,
        autoplay: false,
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
          dynamicBullets: true,

          renderBullet(index, className) {
            return `<span class="${className} swiper-pagination-bullet-custom">${
              index + 1
            }</span>`;
          },
        },
        breakpoints: {
          1024: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          768: {
            slidesPerView: 3,
            slidesPerGroup: 3,
          },
          640: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
          471: {
            slidesPerView: 2,
            slidesPerGroup: 2,
          },
          470: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          250: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
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
.StoreVoucher {
  background-color: $color-background;
  .titel {
    letter-spacing: 0 !important;
    font-size: 22px !important;
    font-weight: 500 !important;
    font-family: $fontfamliy3 !important;
    color: $fontcolor !important;
  }
  .text {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorlinks !important;
    font-weight: 600 !important;

    @media (max-width: 600px) {
      font-size: 14px !important;
    }
  }
  .btn {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    color: $fontcolorsm !important;
    font-size: 14px !important;
    margin: 0 auto !important;
    font-weight: 600;
    background-color: $color-2 !important;
    @media (max-width: 600px) {
      font-size: 13px !important;
    }
  }
}
.swiper {
  height: auto;
  padding-bottom: 45px;
  ::v-deep.swiper-pagination-bullet {
    font-size: 10px;
    width: 15px !important;
    height: 15px !important;
    line-height: 1.5;
    opacity: 0.5;
    background: rgb(223, 223, 223);
    transition: all 0.2s 0s linear;
    color: rgb(82, 82, 82);

    &:hover {
      opacity: 1;
    }

    &.swiper-pagination-bullet-active {
      opacity: 1;
      color: #fff;
      background: $color-2;
    }
  }
}

// .card::after {
//   position: absolute;
//   content: "";
//   height: 20px;
//   right: -10px;
//   border-radius: 40px;
//   z-index: 1;
//   top: 50%;
//   transform: translateY(-50%);
//   background-color: #f8f9fa;
//   width: 20px;
//   // border-left-width: 3px !important;
//   // border-left-style: solid !important;
//   // border-left-color: #ff7043 !important;
//   box-shadow: inset 3px 0 0 0px #81d4fa;
// }

// .card::before {
//   position: absolute;
//   content: "";
//   height: 20px;
//   left: -10px;
//   border-radius: 40px;
//   z-index: 1;
//   top: 50%;
//   transform: translateY(-50%);
//   background-color: #f8f9fa;
//   width: 20px;
//   // border: 2px dashed #ff7043 !important;
//   // border-right-width: 2px !important;
//   // border-left-style: dashed !important;
//   // border-left-color: #ff7043 !important;
//   box-shadow: inset -3px 0 0 0px #81d4fa;
// }

.vertical {
  border-left: 2px dashed #81d4fa;
  height: 100%;
}
.Voucher {
  position: absolute;
  top: 0;
  left: -3px;
  padding: 5px 0;
  z-index: 5;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  li {
    list-style: none;
    width: 8px;
    height: 8px;
    background-color: $color-background;
    border-radius: 30%;
    // border-right: 1px solid #42a5f5;
  }
}
</style>
