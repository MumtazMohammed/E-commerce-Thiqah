<template>
  <v-sheet color="transparent" class="my-2">
    <!-- advertisement  -->
    <v-container class="pa-0 pa-md-0 pa-lg-0 pa-sm-1">
      <!-- TheAdv -->
      <swiper class="swiper" :options="swiperOption">
        <swiper-slide v-for="(item, i) in items" :key="i">
          <v-card
            style="position: absolute"
            width="100%"
            height="100%"
            :color="item.color"
            tile
            flat
          >
          </v-card>
          <v-img contain :src="item.src" :lazy-src="item.src"> </v-img>
        </swiper-slide>
        <!-- <div class="swiper-pagination" slot="pagination"></div> -->
      </swiper>
    </v-container>
  </v-sheet>
</template>
<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

export default {
  name: "AdvertisementTow",
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    return {};
  },
  data() {
    return {
      model: 0,
      items: [
        {
          src: "https://cf.shopee.com.my/file/my-50009109-69f0041a5f226fe98cb3e5ac3eea4474_xxhdpi",
          color: "#e3efff",
        },
        {
          src: "https://cf.shopee.com.my/file/my-50009109-a14a7216a37a383d922cfd8251c8a69d_xxhdpi",
          color: "#ad0401",
        },
        {
          src: "https://cf.shopee.com.my/file/my-50009109-eec5effd28eb8460e26587a0b3e10e74_xxhdpi",
          color: "#fbdd63",
        },
        {
          src: "https://cf.shopee.com.my/file/my-50009109-f04943177921139af489b66bcc4d34af_xxhdpi",
          color: "#13bade",
        },
      ],
      swiperOption: {
        initialSlide: 0,
        freeMode: false,
        effect: "card",
        spaceBetween: 10,
        autoplay: {
          delay: 2500,
          disableOnInteraction: true,
          stopOnLastSlide: false,
        },
        loop: false,
        loopFillGroupWithBlank: false,
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
        breakpoints: {
          1024: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          768: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          640: {
            slidesPerView: 1,
            slidesPerGroup: 1,
          },
          471: {
            slidesPerView: 1,
            slidesPerGroup: 1,
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
};
</script>
<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap");
@import "@/scss/virables";
@import "@/scss/mixin";

.swiper {
  height: 360px !important;
  @media (max-width: 600px) {
    height: 200px !important;
  }

  .swiper-pagination::v-deep .swiper-pagination-bullet {
    width: 10px !important;
    border-radius: 50%;
    height: 10px;
    margin: 0 5px;
    background-color: #eee;
    opacity: 1;
    @media (max-width: 600px) {
      height: 6px;
      width: 6px !important;
    }
  }
  .swiper-pagination::v-deep .swiper-pagination-bullet-active {
    background-color: $color-2;
  }
  ::v-deep.swiper-container {
    @media (max-width: 600px) {
      padding-right: 5px;
      padding-left: 5px;
    }
  }
}
::v-deep .swiper-container-horizontal > .swiper-pagination-bullets {
  bottom: 7px !important;
}

::v-deep .v-image.v-responsive.theme--light {
  height: 360px !important;
  @media (max-width: 600px) {
    height: 200px !important;
  }
}
</style>
