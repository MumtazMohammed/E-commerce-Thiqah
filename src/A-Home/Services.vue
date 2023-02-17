<template>
  <div class="Shape_box">
    <v-container class="py-2 pb-1 px-2 px-md-1 px-lg-1 px-sm-1">
      <!-- <v-card class="mx-auto" style="margin-top: -20px; z-index: 8" height="30" width="80%">
      </v-card> -->
      <v-row no-gutters>
        <v-col>
          <v-card class="my-2" color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="green elevation-3 darken-1 pa-1"
              >
                mdi-taxi
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
              توصيل
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card class="my-2" color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="deep-purple elevation-3 lighten-1 pa-1"
              >
                mdi-car
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
              معرض السيارات
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card class="my-2" color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="indigo elevation-3 lighten-1 pa-1"
              >
                mdi-home-silo
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
              العقارات
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card class="my-2" color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="blue elevation-3 darken-1 pa-1"
              >
                mdi-earth
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
              السفريات
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card class="my-2" color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="brown elevation-3 lighten-1 pa-1"
              >
                mdi-cog-transfer
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
              خدمات هندسية
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      <v-row no-gutters class="mb-3">
        <v-col>
          <v-card color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="green elevation-3 accent-4 pa-1"
              >
                mdi-cart-variant
              </v-icon>
              <v-card-text style="height: 40px" class="text px-1 mt-1 pa-0">
                سوبر ماركت
              </v-card-text>
            </v-row>
          </v-card>
        </v-col>
        <v-col>
          <v-card color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="yellow elevation-3 darken-4 pa-1"
              >
                mdi-food
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text mt-1 px-1 pa-0">
              المطاعم
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="pink elevation-3 darken-1 pa-1"
              >
                mdi-shopping
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text mt-1 px-1 pa-0">
              ثقة مول
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="blue-grey elevation-3 darken-2 pa-1"
              >
                mdi-cellphone-message
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text mt-1 pa-0 px-1"
              >فواتير & رصيد
            </v-card-text>
          </v-card>
        </v-col>
        <v-col>
          <v-card color="transparent" elevation="0">
            <v-row no-gutters justify="center" align="center">
              <v-icon
                style="border-radius: 50%"
                size="30"
                color="#eee"
                class="teal elevation-3 accent-4 pa-1"
              >
                mdi-code-greater-than-or-equal
              </v-icon>
            </v-row>
            <v-card-text style="height: 40px" class="text mt-1 pa-0 px-1"
              >خدمات برمجية
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
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
export default {
  name: "CarShape",
  components: {},
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
    font-size: 12px !important;
  }
}
</style>
