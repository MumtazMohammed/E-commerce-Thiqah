<template>
  <div class="Cars">
    <v-container>
      <v-row>
        <v-col cols="12" class="py-0">
          <div class="d-flex">
            <div class="d-flex align-center ma-2">
              <span class="dot-trusted"></span>
              <v-card-subtitle class="pa-0 pr-2"> موثق </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-Nottrusted"></span>
              <v-card-subtitle class="pa-0 pr-2"> غير موثق </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-upgrade"></span>
              <v-card-subtitle class="pa-0 pr-2"> مترقي </v-card-subtitle>
            </div>
            <div class="d-flex align-center ma-2">
              <span class="dot-feature"></span>
              <v-card-subtitle class="pa-0 pr-2"> معزز </v-card-subtitle>
            </div>
          </div>
        </v-col>
        <!-- search for Cars -->
        <v-col cols="12">
          <v-card-actions class="justify-center">
            <v-card
              flat
              outlined
              class="search-card d-flex align-center overflow-hidden"
              width="500"
            >
              <!-- delete text  -->
              <v-btn
                v-if="search.length > 0"
                small
                icon
                color="white"
                class="mr-1 red darken-1"
                @click="reset()"
              >
                <v-icon class="">mdi-close</v-icon>
              </v-btn>
              <!-- customiza search -->
              <v-text-field
                class="rounded-b-0"
                v-model="search"
                solo
                large
                flat
                label="بحث عن سيارة ؟"
                hide-details="true"
                background-color="#fff"
                append-icon="mdi-store-search-outline"
              ></v-text-field>
            </v-card>
          </v-card-actions>
        </v-col>
        <!-- Cars Cards  -->
        <v-col cols="12" md="4" sm="6" v-for="Car in Cars" :key="Car.id">
          <v-sheet color="transparent">
            <v-card-actions class="py-0 justify-space-between">
              <v-card-subtitle class="pa-0"> محجوز </v-card-subtitle>
              <div class="d-flex">
                <span class="dot-trusted mx-1"></span>
                <span class="dot-Nottrusted mx-1"></span>
                <span class="dot-feature mx-1"></span>
                <span class="dot-upgrade mx-1"></span>
              </div>
            </v-card-actions>
          </v-sheet>
          <v-card
            :to="{
              name: 'UserCarDetails',
              params: {
                carId: Car.id,
              },
            }"
            outlined
            class="overflow-hidden"
          >
            <v-row>
              <v-col cols="3">
                <v-avatar tile size="70" color="grey darken-4">
                  <v-img
                    contain
                    :src="getimageUrl(Car.folder, Car.image)"
                    :lazy-src="getimageUrl(Car.folder, Car.image)"
                    :alt="getimageUrl(Car.folder, Car.image)"
                  />
                </v-avatar>
              </v-col>
              <v-col cols="9">
                <v-card-text class="text text-center py-1"
                  >{{ Car.id }}
                </v-card-text>
                <v-card-text class="text text-center py-1"> معرض </v-card-text>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Cars from "@/data-json/All-Car.json";
export default {
  name: "Cars",
  data() {
    return {
      Cars,
      search: "",
      carId: this.$route.params.CarType,
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
    reset() {
      return (this.search = "");
    },
  },
  computed: {
    filteredStore: function () {
      return this.Cars.filter((showroom) => {
        return showroom.id.match(this.search);
      });
    },

    length() {
      return 7000;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Cars {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
  padding: $padding;
  font-family: $fontfamliy;
  letter-spacing: 0px;
  .text {
    font-family: $fontfamliy !important;
    letter-spacing: 0px;
    font-weight: 500;
  }
  .dot-trusted {
    width: 8.5px;
    height: 8.5px;
    display: block;
    background-color: #43a047;
    border-radius: 50%;
  }
  .dot-Nottrusted {
    width: 8.5px;
    height: 8.5px;
    display: block;
    background-color: #d23819;
    border-radius: 50%;
  }
  .dot-upgrade {
    width: 8.5px;
    height: 8.5px;
    display: block;
    background-color: #40c4ff;
    border-radius: 50%;
  }
  .dot-feature {
    width: 8.5px;
    height: 8.5px;
    display: block;
    background-color: #f57c00;
    border-radius: 50%;
  }
}
</style>
