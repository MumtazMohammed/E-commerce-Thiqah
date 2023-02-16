<template>
  <v-sheet class="wrap">
    <!-- advertisement  -->
    <v-container class="pa-2 pa-md-0 pa-lg-0 pa-sm-1">
      <v-row no-gutters>
        <!-- TheCategories -->
        <v-col cols="2" class="hidden-sm-and-down">
          <!-- first List  -->
          <v-card tile flat color="" height="100%">
            <v-menu
              allow-overflow
              tile
              class="elevation-0 pa-0"
              open-on-hover
              left
              center
              offset-x
            >
              <template v-slot:activator="{ on, attrs }">
                <v-list class="py-0" link color="transparent">
                  <v-list-item
                    link
                    v-bind="attrs"
                    v-on="on"
                    v-for="(item, index) in Categories"
                    :key="index"
                  >
                    <v-list-item-title class="link">
                      {{ item.tital }}
                    </v-list-item-title>
                    <v-icon small>mdi-arrow-left</v-icon>
                  </v-list-item>
                </v-list>
              </template>
              <!-- second List  -->
              <v-card
                style="overflow: hidden"
                outlined
                tile
                height="360"
                width="195"
              >
                <v-menu
                  flat
                  allow-overflow
                  tile
                  open-on-hover
                  left
                  nudge-left="0"
                  nudge-top="1"
                  center
                  offset-x
                >
                  <template v-slot:activator="{ on, attrs }">
                    <v-list class="py-0" link color="transparent">
                      <v-list-item
                        link
                        v-bind="attrs"
                        v-on="on"
                        v-for="(item, index) in Categories"
                        :key="index"
                      >
                        <v-list-item-title class="link">
                          {{ item.tital }}
                        </v-list-item-title>
                        <v-icon small>mdi-arrow-left</v-icon>
                      </v-list-item>
                    </v-list>
                  </template>
                  <!-- third List  -->
                  <v-card outlined tile height="361" width="195">
                    <v-list class="py-0" link color="transparent">
                      <v-list-item
                        link
                        v-bind="attrs"
                        v-on="on"
                        v-for="(item, index) in Categories"
                        :key="index"
                      >
                        <v-list-item-title class="link">
                          {{ item.tital }}
                        </v-list-item-title>
                      </v-list-item>
                    </v-list>
                  </v-card>
                </v-menu>
              </v-card>
            </v-menu>
          </v-card>
        </v-col>
        <!-- TheAdv -->
        <v-col cols="12" md="10" lg="10" xl="10" class="pa-0">
          <v-card class="hidden-sm-and-down" tile flat>
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
              <div class="swiper-pagination" slot="pagination"></div>
            </swiper>
          </v-card>
          <v-card class="hidden-md-and-up" flat>
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
              <div class="swiper-pagination" slot="pagination"></div>
            </swiper>
          </v-card>
        </v-col>
      </v-row>
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
      itemss: [
        { title: "Click Me" },
        { title: "Click Me" },
        { title: "Click Me" },
        { title: "Click Me 2" },
      ],
      Categories: [
        {
          tital: "كمبيوتر وملحقاتها",
        },
        {
          tital: "الجولات والأجهزة اللوحية ",
        },
        {
          tital: "الأزياء",
        },
        {
          tital: "الصحة & الجمال",
        },
        {
          tital: "اثاث منزلية & مكتبية ",
        },
        {
          tital: "ألعاب",
        },
        {
          tital: " البقالة",
        },
        {
          tital: " منتجات الأطفال",
        },
        {
          tital: " البناء والكهرباء",
        },
        {
          tital: " القرطاسية ",
        },
        {
          tital: "المركبات",
        },
        {
          tital: " عقارات",
        },
      ],
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
.wrap {
  background-color: #e64a19 !important;
  @media (max-width: 960px) {
    background-color: $color-background !important;
  }
}
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
::v-deep .container.pa-2.pa-md-0.pa-lg-0.pa-sm-1 {
  @media (max-width: 960px) {
    padding-bottom: 0 !important;
  }
}
::v-deep .v-image.v-responsive.theme--light {
  height: 360px !important;
  @media (max-width: 600px) {
    height: 200px !important;
  }
}
.AdvertisementTow {
  height: 330px !important;
  @media (max-width: 600px) {
    border-radius: 0px !important;
    height: 200px !important;
  }
}
::v-deep.swiper-pagination.swiper-pagination-clickable.swiper-pagination-bullets {
  bottom: 0;
}
::v-deep.v-menu__content.theme--light.rounded-0.menuable__content__active {
  box-shadow: 0 0 0 0 !important;
}
::v-deep .v-list-item {
  min-height: 30px;
}
::v-deep .v-list-item:hover .link {
  // font-size: 14px;
  color: $color-2;
}
::v-deep .v-list-item:hover .v-icon {
  color: $color-2;
}
.link {
  font-family: $fontfamliy3;
  font-size: 13px;
}
</style>
