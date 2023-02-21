<template>
  <div class="client-store">
    <!-- client Card -->
    <v-card
      style="background: linear-gradient(180deg, #ffccbc 0%, #eee 100%)"
      flat
      class="mx-auto grey"
      tile
    >
      <v-container>
        <!-- client Card -->
        <v-row align="center" justify="center" no-gutters class="fill-height">
          <v-avatar class="profile" color="grey" size="60">
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <v-col cols="7" md="10" sm="9" lg="10">
            <v-list-item color="grey">
              <v-list-item-content>
                <v-list-item-title class="text text-h6"
                  >محمد أمي
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-row justify="space-around" no-gutters>
            <v-badge bordered left overlap content="3">
              <v-btn
                :to="{
                  name: 'SmallScreenNotification',
                  params: { Notfication: 'الأشعارات' },
                }"
                exact-path
                depressed
                width="36"
                height="36"
                class="btn-noti-cart"
                fab
              >
                <v-icon> mdi-bell </v-icon>
              </v-btn>
            </v-badge>
            <v-btn depressed width="36" height="36" fab class="btn-noti-cart">
              <v-icon >mdi-dots-vertical </v-icon>
            </v-btn>
          </v-row>
        </v-row>
        <!-- quick information  -->
        <v-row align="center" no-gutters class="fill-height mt-6">
          <v-col v-for="(First, i) in FirstAccess" :key="i">
            <v-card-text
              class="pa-0 text-center"
              v-text="First.cunt"
            ></v-card-text>
            <v-card-text
              class="pa-0 mt-1 text text-center"
              v-text="First.title"
            ></v-card-text>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
    <v-container class="py-0">
      <!-- order  -->

      <v-card flat class="pa-2 my-2">
        <v-card-text class="pt-2 card-titel"> طلبياتي </v-card-text>
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1" v-for="(Second, i) in SecondAccess" :key="i">
            <v-card
              flat
              link
              exact-path
              router
              :to="{
                name: 'SmallScreenClientOrderPage',
                params: { Order: 'مشترياتي' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon
                  :style="Second.flib"
                  class="pa- text-center"
                  color="#fc624d"
                  size="27"
                  v-text="Second.cunt"
                ></v-icon>
              </v-row>
              <v-card-text
                style="height: 45px"
                class="pa-0 mt-2 text text-center"
                v-text="Second.title"
              ></v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- row for card and other  -->
      <v-card flat class="pa-2 my-2">
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1">
            <v-card
              flat
              :to="{
                name: 'SmallScreenClientCartPage',
                params: { Cart: 'مشترياتي' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon
                  style="
                    padding: 5px;
                    border-radius: 50%;
                    background-color: #fc624d;
                  "
                  class="grey lighten-3"
                  color="#fc624d"
                  size="27"
                  v-text="`mdi-cart-outline`"
                ></v-icon>
              </v-row>
              <v-card-text
                class="pa-0 mt-2 text text-center"
                v-text="`سلة التسوق `"
              ></v-card-text>
            </v-card>
          </v-col>
          <v-col class="px-1" v-for="(Third, i) in ThirdAccess" :key="i">
            <v-row justify="center" no-gutters class="fill-height">
              <v-icon
                :style="Third.flib"
                style="
                  padding: 5px;
                  border-radius: 50%;
                  background-color: #fc624d;
                "
                class="pa- text-center"
                :class="Third.color"
                color="white"
                size="27"
                v-text="Third.cunt"
              ></v-icon>
            </v-row>
            <v-card-text
              class="pa-0 mt-2 text text-center"
              v-text="Third.title"
            ></v-card-text>
          </v-col>
        </v-row>
      </v-card>
      <!-- wallet  -->
      <v-card flat class="pa-2 my-2">
        <v-card-text class="pt-2 card-titel">
          رصيدي
          <v-icon size="22" color="#fc624d" class="mr-1">mdi-wallet</v-icon>
        </v-card-text>
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1 text-center">
            <v-row justify="center" no-gutters class="fill-height">
              <span>0.00</span>
            </v-row>
            <v-card-text
              style="height: 50px"
              class="pa-0 mt-1 text text-center"
            >
              ريال
              <v-chip
                style="display: block"
                small
                class="text px-1"
                color="blue"
                text-color="white"
              >
                تحويل
              </v-chip>
            </v-card-text>
          </v-col>
          <v-col class="px-1">
            <v-row justify="center" no-gutters class="fill-height">
              <span>2</span>
            </v-row>
            <v-card-text
              style="height: 50px"
              class="pa-0 mt-1 text text-center"
            >
              خيار الدفع
            </v-card-text>
          </v-col>
          <v-col class="px-1">
            <v-row justify="center" no-gutters class="fill-height">
              <span>20</span>
            </v-row>
            <v-card-text
              style="height: 50px"
              class="pa-0 mt-1 text text-center"
            >
              سجل التحويلات
            </v-card-text>
          </v-col>
        </v-row>
      </v-card>
      <!-- wallet  -->
      <v-card flat class="pa-2 my-2">
        <v-row align="center" no-gutters class="fill-height mb-5">
          <v-col class="px-1" v-for="(Fift, i) in FifthhAccess" :key="i">
            <v-row justify="center" no-gutters class="fill-height">
              <v-icon
                :style="Fift.flib"
                color="grey darken-2"
                size="27"
                v-text="Fift.cunt"
              ></v-icon>
            </v-row>
            <v-card-text
              class="pa-0 mt-1 text text-center"
              v-text="Fift.title"
            ></v-card-text>
          </v-col>
        </v-row>
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1" v-for="(Sixth, i) in SixthAccess" :key="i">
            <v-row justify="center" no-gutters class="fill-height">
              <v-icon
                :style="Sixth.flib"
                class="pa- text-center"
                color="grey darken-2"
                size="27"
                v-text="Sixth.cunt"
              ></v-icon>
            </v-row>
            <v-card-text
              class="pa-0 mt-1 text text-center"
              v-text="Sixth.title"
            ></v-card-text>
          </v-col>
        </v-row>
      </v-card>
      <v-sheet class="my-2" min-height="200">
        <v-card-text class="card-titel-follow">متابع : </v-card-text>
        <v-row class="px-3" no-gutters>
          <v-col class="pa-1" v-for="i in 18" :key="i" cols="2">
            <v-row justify="center" no-gutters>
              <v-avatar size="50px">
                <img
                  alt="Avatar"
                  src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
                />
              </v-avatar>
            </v-row>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- <Services /> -->
    </v-container>
  </div>
</template>
<script>
// import Services from "@/A-Home/Services.vue";

export default {
  name: "NormalUserPage",
  //   components: { Services },
  // components: { NavigationUser },
  data() {
    return {
      drawer: true,
      FirstAccess: [
        { title: "المفضلة", cunt: "1" },
        { title: "شوهدت مؤخرا", cunt: "50" },
        { title: "النقاط", cunt: "1" },
        { title: "القسائم", cunt: "1" },
      ],
      SecondAccess: [
        {
          title: " شحن المنتج",
          cunt: "mdi-package",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "استلام المنتج",
          cunt: "mdi-truck-delivery ",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "تقييم المنتج",
          cunt: "mdi-message-draw ",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "المرتجع & والإلغاء",
          cunt: "mdi-archive-cancel",
        },
      ],
      ThirdAccess: [
        {
          title: " ثقة مول ",
          cunt: "mdi-shopping",
        },
        {
          title: "شارك وأربح",
          cunt: "mdi-link-box",
          color: "grey",
        },
        {
          title: "أفتح متجر",
          cunt: "mdi-handshake ",
          flib: "  transform: scaleX(-1)",
          color: "indigo lighten-1 ",
        },
        // {
        //   title: "المرتجع & والإلغاء",
        //   cunt: "mdi-archive-cancel",
        // },
      ],

      FifthhAccess: [
        {
          title: "  تقييمي ",
          cunt: "mdi-comment-text-outline",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "مساعدة ",
          cunt: "mdi-help-circle-outline",
        },
        {
          title: "شوهدت مؤخرا",
          cunt: "mdi-history ",
        },
      ],
      SixthAccess: [
        {
          title: " عضوية",
          cunt: "mdi-card-account-details-star-outline ",
        },
        {
          title: " تعبئة رصيد",
          cunt: "mdi-cellphone-arrow-down mdi-rotate-180 ",
        },
        {
          title: "خدمة العملاء",
          cunt: "mdi-face-agent ",
          flib: "  transform: scaleX(-1)",
        },
      ],
      mini: true,
    };
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.client-store {
  background-color: #eee;
  width: 100%;
  min-height: 100vh;
  @media (max-width: 960px) {
    margin-bottom: 50px;
  }
}
.v-list-item__title.text.text-h6 {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
}
.text {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 500;
  font-size: 14px !important;
}
.card-titel {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  font-size: 17px;
}
.card-titel-follow {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 500;
  font-size: 17px;
}

::v-deep span.v-badge__badge {
  color: #fff !important;
  background-color: $color-2 !important;
  // min-width: 15px;
  height: 18px;
  // padding: 5px;
  // display: flex;
  // justify-content: center;
  // align-items: center;
  border: 0 !important;
  // font-size: 13px !important;
  @media (max-width: 600px) {
    font-size: 11px !important;
  }
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border: 0 !important;
}
.btn-noti-cart {
  color: $color-2 !important;
  // background-color: #eee;
  @media (max-width: 600px) {
    font-size: 20px !important;
  }
}
</style>
