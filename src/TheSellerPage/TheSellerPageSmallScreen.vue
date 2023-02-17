<template>
  <div class="client-store">
    <v-card
      style="background: linear-gradient(180deg, #2196f3 0%, #f8f9fa 100%)"
      flat
      class="mx-auto grey"
      tile
    >
      <v-container>
        <v-row align="center" no-gutters class="fill-height">
          <v-avatar class="profile" color="grey" size="60">
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <v-col cols="8">
            <v-list-item color="grey">
              <v-list-item-content>
                <v-list-item-title class="text text-h6"
                  >محمد أمين
                </v-list-item-title>
                <v-list-item-subtitle> j </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-spacer></v-spacer>
          <v-btn icon class="white">
            <v-icon color="#fc624d">mdi-dots-horizontal </v-icon>
          </v-btn>
        </v-row>
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
      <v-card flat class="pa-2 mb-2">
        <v-card-text class="pt-2 card-titel"> طلبات العملاء </v-card-text>
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-2" v-for="(Second, i) in SecondAccess" :key="i">
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
                  color="blue"
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
      <v-card flat class="pa-2 mb-2">
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
      <v-card flat class="pa-2 mb-2">
        <v-card-text class="pt-2 card-titel">
          محفظتي
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
      <v-row no-gutters class="mb-3">
        <v-col class="pl-1">
          <v-card flat color="deep-purple lighten-1">
            <v-row justify="center" no-gutters class="fill-height">
              <span class="card-points-vou-cunt">2</span>
            </v-row>
            <v-card-title
              style="height: 30px"
              class="pa-0 card-points-vou justify-center"
            >
              نقطة
            </v-card-title>
          </v-card>
        </v-col>
        <v-col class="pr-1">
          <v-card color="indigo lighten-1" flat>
            <v-row justify="center" no-gutters class="fill-height">
              <span class="card-points-vou-cunt">2</span>
            </v-row>
            <v-card-title
              style="height: 30px"
              class="pa-0 card-points-vou justify-center"
            >
              قسيمة
            </v-card-title>
          </v-card>
        </v-col>
      </v-row>
      <v-card flat class="pa-2 mb-2">
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
      <v-sheet class="mb-2" min-height="200">
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
          title: "طلبات جديدة",
          cunt: "mdi-basket",
          // flib: "  transform: scaleX(-1)",
        },
        {
          title: "بإنتظار شحن المنتج",
          cunt: "mdi-truck-delivery ",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "طلبات ألغيت",
          cunt: "mdi-basket-remove",
          flib: "  transform: scaleX(-1)",
        },
        {
          title: "تقييمات العملاء",
          cunt: "mdi-comment-multiple",
          flib: "  transform: scaleX(-1)",
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
  background-color: $color-background;
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
.card-points-vou {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  color: #fff !important;
  font-size: 17px !important;
  font-weight: 500;
}
.card-points-vou-cunt {
  font-family: sans-serif !important;
  color: #fff !important;
  font-size: 23px !important;
  font-weight: 700;
}
</style>
