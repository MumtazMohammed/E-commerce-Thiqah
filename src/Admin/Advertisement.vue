<template>
  <div class="Advertisement">
    <v-container>
      <v-card class="pa-2">
        <v-img contain min-height="150" min-width="200" :src="ActiveImage">
        </v-img>
      </v-card>
    </v-container>
    <v-row class="justify-center">
      <v-col cols="12">
        <v-chip-group
          show-arrows
          center-active
          active-class="blue white--text "
        >
          <div class="pa-1 ma-1 card-chip" v-for="(item, i) in items" :key="i">
            <v-btn small dark icon class="red darken-1">
              <v-icon>mdi-close</v-icon>
            </v-btn>
            <v-chip @click="ActiveImage = item.src" class="chip ma-1">
              {{ item.text }}
            </v-chip>
          </div>
        </v-chip-group>
      </v-col>
      <!-- image select  -->
      <v-col cols="12" md="6" sm="6">
        <v-card>
          <v-text-field
            label="  عنوان الصورة"
            :hide-details="true"
            single-line
            filled
          ></v-text-field>
          <v-file-input
            label="أختيار صورة"
            filled
            :show-size="1000"
            :hide-details="true"
          >
            <template v-slot:selection="{ index, text }">
              <v-chip
                v-if="index < 6"
                color="blue accent-4"
                dark
                label
                small
                draggable
              >
                {{ text }}
              </v-chip>
            </template>
          </v-file-input>
        </v-card>
        <v-card-actions class="justify-center">
          <v-btn width="300" class="btn-upload success">نشر</v-btn>
        </v-card-actions>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      ActiveImage: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
      items: [
        {
          text: "إعلان موقع 1",
          src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
        },
        {
          text: "إعلان موقع 2",
          src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
        },
        {
          text: "إعلان شركة أدهن ",
          src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
        },
        {
          text: "إعلان شركة تئمينات الحياء ",
          src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Advertisement {
  padding: $padding;
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
}
.chip {
  font-family: $fontfamliy !important;
  letter-spacing: 0px;
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy !important;
  letter-spacing: 0px;
}
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
::v-deep .v-slide-group__content {
  justify-content: center;
}
::v-deep .v-btn--icon.v-size--small {
  height: 20px;
  width: 20px;
}
::v-deep .v-btn--icon.v-size--small .v-icon {
  font-size: 18px;
}
::v-deep .v-input {
  justify-content: center;
}
::v-deep .v-input__prepend-outer {
  display: none;
}
.carouselItem {
  transition: all 1s ease;
}
.card-chip {
  box-shadow: 0 3px 1px -2px rgb(0 0 0 / 20%), 0 2px 2px 0 rgb(0 0 0 / 14%),
    0 1px 5px 0 rgb(0 0 0 / 12%);
  border-radius: 10px;
}
.btn-upload {
  font-family: $fontfamliy !important;
  letter-spacing: 0px;
  font-size: 18px !important;
}
</style>
