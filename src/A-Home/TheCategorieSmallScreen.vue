<template>
  <div class="Registration mt-2">
    <v-container class="py-0 px-1">
      <div class="tital pa-2">
        جميع
        <strong class="mx-1">الفئات</strong>
      </div>
      <!-- <span class="line my-3 mx-auto"></span> -->
      <swiper class="swiperR" :options="swiperOption">
        <swiper-slide v-for="(Categorie, index) in Categories" :key="index">
          <v-card
            min-width="100%"
            max-width="180px"
            color="#fff"
            class="d-flex ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
          >
            <v-avatar class="icon" size="60px" tile>
              <v-img
                contain
                :src="getimageUrl(Categorie.folder, Categorie.imgOne)"
              ></v-img>
            </v-avatar>

            <v-card-text
              class="pa-0 px-1 text-center card-text"
              v-text="Categorie.titalOne"
            >
            </v-card-text>
          </v-card>
          <v-card
            min-width="100%"
            class="d-flex mt-1 ServiceCard align-center justify-space-between flex-column"
            to="/Products"
            router
            flat
          >
            <v-avatar class="icon" size="60px" tile>
              <v-img
                contain
                :src="getimageUrl(Categorie.folder, Categorie.imgTow)"
              ></v-img>
            </v-avatar>
            <v-card-text
              class="pa-0 px-1 text-center card-text"
              v-text="Categorie.titalTow"
            >
            </v-card-text>
          </v-card>
        </swiper-slide>
        <div
          class="swiper-pagination swiper-pagination-bullets"
          slot="pagination"
        ></div>
      </swiper>
    </v-container>
  </div>
</template>

<script>
import VerifiedCar from "../data-json/All-Car.json";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";
export default {
  name: "ShowVerifiedCar",
  title: "Loop mode with multiple slides per group",
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
      Categories: [
        {
          titalOne: "الجولات والأجهزة اللوحية ",
          imgOne: "mobile.png",
          titalTow: "كمبيوتر وملحقاتها",
          imgTow: "computing.png",
          folder: "categories",
        },
        {
          imgOne: "Fashion.png",
          imgTow: "health-beauty.png",
          folder: "categories",
          titalOne: "الأزياء",
          titalTow: "الصحة & الجمال",
        },
        {
          imgOne: "furniture.png",
          imgTow: "game.png",
          folder: "categories",
          titalOne: "اثاث منزلية & مكتبية ",
          titalTow: "ألعاب",
        },
        {
          imgOne: "grocery.png",
          imgTow: "baby.png",
          folder: "categories",
          titalOne: " البقالة",
          titalTow: " منتجات الأطفال",
        },
        {
          imgOne: "librry.png",
          imgTow: "Electricity.png",
          folder: "categories",
          titalTow: " البناء والكهرباء",
          titalOne: " القرطاسية ",
        },
        {
          imgOne: "vehicles.png",
          imgTow: "real-estates.png",
          folder: "categories",
          titalOne: "المركبات",
          titalTow: " عقارات",
        },
      ],

      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "cards",
        spaceBetween: 6,
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
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          470: {
            slidesPerView: 4,
            slidesPerGroup: 4,
          },
          250: {
            slidesPerView: 4,
            slidesPerGroup: 4,
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
.Registration {
  width: 100%;
  min-height: 20vh;
  display: flex;
  justify-content: center;
  // align-items: center;
  background-color: $color-background;
  font-family: $fontfamliy;

  .ServiceCard {
    position: relative;
  }
  .swiperR {
    height: 240px;
    @media (max-width: 700px) {
      height: 215px;
    }
    .swiper-slide {
      height: 200px;
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

  .card-text {
    font-family: $fontfamliy3;
    letter-spacing: 0;
    font-size: 13px;
    font-weight: 600;
    color: $fontcolorlinks !important;
    height: 40px !important;
    align-items: center;
    display: flex;
    justify-content: center;
    @media (max-width: 600px) {
      font-size: 12px;
      height: 40px !important;
    }
  }
  .tital {
    position: relative;
    text-align: center;
    font-family: $fontfamliy3;
    font-size: 22px;
    color: $color-2;
    font-weight: 600;
    // background-color: aqua;
    @media (max-width: 600px) {
      font-size: 18px;
      // padding-top: 0 !important;
    }
    @media (max-width: 350px) {
      font-size: 17px;
    }
  }
  // .tital::before {
  //   content: "";
  //   position: absolute;
  //   top: 50%;
  //   left: 0;
  //   opacity: 0.9;
  //   background-color: #eee;
  //   width: 40%;
  //   height: 2.2px;
  //   @media (max-width: 850px) {
  //     width: 35%;
  //   }
  //   @media (max-width: 650px) {
  //     width: 30%;
  //   }
  //   @media (max-width: 430px) {
  //     width: 26% !important;
  //   }
  // }
  // .tital::after {
  //   content: "";
  //   position: absolute;
  //   top: 50%;
  //   right: 0;
  //   opacity: 0.9;
  //   background-color: #eee;
  //   width: 40%;
  //   height: 2.2px;
  //   @media (max-width: 850px) {
  //     width: 35%;
  //   }
  //   @media (max-width: 650px) {
  //     width: 30%;
  //   }
  //   @media (max-width: 430px) {
  //     width: 26%;
  //   }
  // }
}
::v-deep .v-avatar {
  @media (max-width: 600px) {
    height: 50px !important;
    min-width: 50px !important;
    width: 50px !important;
  }
}
</style>
