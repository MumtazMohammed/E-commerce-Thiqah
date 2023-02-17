<template>
  <div class="SpicalShowRoom py-2">
    <v-container class="pa-1">
      <div class="pa-2 tital">
        الشركات
        <strong class="mx-1">التجارية</strong>
      </div>
      <v-row no-gutters class="">
        <v-col
          md="2"
          sm="4"
          lg="2"
          cols="6"
          class="pa-1"
          v-for="i in 6"
          :key="i"
        >
          <v-card outlined to="/SellerStorePage" class="mx-auto">
            <v-img height="150" contain src="../assets/outsrc/adidas-logo.png">
            </v-img>
            <!-- <v-card-text class="py-2" style="position: relative">
              <v-card-actions class="justify-center pa-0">
                <v-btn
                  color="#fc624d"
                  class="white--text brand elevation-0"
                  small
                  to="/SellerStorePage"
                  block
                >
                  أديداس
                </v-btn>
              </v-card-actions>
            </v-card-text> -->
          </v-card>
        </v-col>
      </v-row>
      <!-- small screen view -->
    </v-container>
  </div>
</template>

<script>
import featuredshowrooms from "../data-json/showroom.json";

export default {
  name: "SpicalShowRoom",
  components: {},

  data() {
    return {
      Tital: "المعارض المتميزة",
      featuredshowrooms,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
  },
  computed: {
    getCarInfo() {
      let GetShowroomfeatured = [];
      for (let i = 0; i < this.featuredshowrooms.length; i++) {
        if (this.featuredshowrooms[i].featured == true) {
          GetShowroomfeatured.push(this.featuredshowrooms[i]);
        }
      }
      return GetShowroomfeatured;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.SpicalShowRoom {
  width: 100%;
  background-color: $color-background;
  .tital {
    position: relative;
    text-align: center;
    font-family: $fontfamliy3;
    font-size: 22px;
    color: $color-2;
    font-weight: 600;
    pointer-events: none;
    @media (max-width: 600px) {
      font-size: 18px;
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
  //     width: 25%;
  //   }
  //   @media (max-width: 360px) {
  //     width: 20%;
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
  //     width: 25%;
  //   }
  //   @media (max-width: 360px) {
  //     width: 20%;
  //   }
  // }
}

.brand {
  font-size: 18px;
  text-align: center !important;
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-weight: 600 !important;
  color: $color-2;
  @media (max-width: 600px) {
    font-size: 16px;
  }
}
::v-deep .v-image.v-responsive.theme--light {
  @media (max-width: 600px) {
    height: 100px !important;
  }
}
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
</style>
