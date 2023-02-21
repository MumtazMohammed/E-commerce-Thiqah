<template>
  <div class="client-store">
    <v-card
      style="background: linear-gradient(180deg, #ff7043 0%, #fbe9e7 80%)"
      flat
      class="mx-auto grey"
      tile
    >
      <v-container class="py-0">
        <v-row align="center" no-gutters class="fill-height">
          <v-avatar class="profile" color="grey" size="60">
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <v-col cols="7" md="10" sm="9" lg="10">
            <v-list-item color="grey">
              <v-list-item-content>
                <v-list-item-title class="text mb-2 text-h6">
                  محمد أمين
                </v-list-item-title>
                <v-list-item-subtitle>
                  <v-card
                    class="overflow-hidden"
                    flat
                    rounded="sm"
                    max-width="170"
                  >
                    <v-row align="center" class="fill-height" no-gutters>
                      <span class="store-with-thiah white--text red">
                        ثقة مول
                      </span>
                      <v-icon color="red" class="mx-1">
                        mdi-check-decagram
                      </v-icon>
                      <span class="store-with-thiah black--text">
                        بائع مرخص
                      </span>
                    </v-row>
                  </v-card>
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-spacer></v-spacer>
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
                <v-icon > mdi-bell </v-icon>
              </v-btn>
            </v-badge>
            <v-btn depressed width="36" height="36" fab class="btn-noti-cart">
              <v-icon >mdi-dots-vertical </v-icon>
            </v-btn>
          </v-row>
        </v-row>
        <v-row align="center" no-gutters class="fill-height mt-6">
          <v-col v-for="(First, i) in FirstAccess" :key="i">
            <v-card-text
              class="pa-0 text-center"
              v-text="First.cunt"
            ></v-card-text>
            <v-card-text
              style="height: 60px"
              class="pa-2 text text-center"
              v-text="First.title"
            ></v-card-text>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
    <v-container class="pt-0">
      <!-- order  -->
      <!-- <v-card rounded="lg" flat class="pa-2 my-3">
        <v-card-text class="pa-3 card-titel"> الوظائف الأساسية</v-card-text>
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-2" v-for="(Second, i) in Order" :key="i">
            <v-card
              flat
              link
              exact-path
              router
              :to="{
                name: 'MyOrder',
                params: { Order: 'الطلبات' },
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
      </v-card> -->
      <!-- links   -->
      <v-card rounded="lg" flat class="pa-1 py-2 mb-3">
        <v-card-text class="pa-2 pt-0 card-titel">
          الوظائف الأساسية</v-card-text
        >
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1" v-for="item in MenuLinks" :key="item">
            <v-card
              flat
              rounded="lg"
              class="my-1 menu-card"
              link
              exact-path
              :to="item.RouterName"
            >
              <v-row no-gutters class="pa-0 pt-1 justify-center">
                <v-icon
                  :color="item.class"
                  class="icon"
                  v-text="item.icon"
                ></v-icon>
              </v-row>
              <span class="link mt-2" v-text="item.link"></span>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- links   -->
      <v-card rounded="lg" flat class="pa-1 py-2 my-3">
        <v-row align="center" no-gutters class="fill-height">
          <v-col class="px-1" v-for="item in MyStore" :key="item">
            <v-card
              flat
              rounded="lg"
              class="my-1 menu-card"
              link
              exact-path
              :to="item.RouterName"
            >
              <v-row no-gutters class="pa-0 pt-1 justify-center">
                <v-icon
                  :color="item.class"
                  class="icon"
                  v-text="item.icon"
                ></v-icon>
              </v-row>
              <span class="link mt-2" v-text="item.link"></span>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- Marketing Tools  -->
      <v-card rounded="lg" flat class="pa-2 my-3">
        <v-card-text class="pa-3 card-titel">أدوات التسويق </v-card-text>
        <v-row align="center" no-gutters class="fill-height">
          <v-col
            cols="4"
            sm="3"
            class="pa-2"
            v-for="item in MarketingTools"
            :key="item"
          >
            <v-card
              flat
              rounded="lg"
              class="my-1 menu-card"
              link
              exact-path
              :to="item.RouterName"
            >
              <v-row no-gutters class="pa-0 pt-1 justify-center">
                <v-avatar
                  class="profile"
                  color="deep-orange lighten-5"
                  size="50"
                >
                  <v-icon size="30" color="deep-orange">
                    {{ item.icon }}
                  </v-icon>
                </v-avatar>
              </v-row>
              <span class="link mt-2" v-text="item.title"></span>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- second row card  -->
      <v-card rounded="lg" flat class="pa-2 mt-3">
        <v-row align="center" no-gutters class="fill-height">
          <v-col
            cols="4"
            class="pa-2"
            v-for="(Fift, i) in FifthhAccess"
            :key="i"
          >
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
      </v-card>
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
        { title: "طلبات جديدة", cunt: "1" },
        { title: "أعلى منتجات تم بيعها", cunt: "1" },
        { title: "عدد الزائرين", cunt: "50" },
        { title: "المتابعين", cunt: "1" },
      ],
      Order: [
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
      MenuLinks: [
        {
          link: "إضافة  ",
          icon: "mdi-basket-plus",
          class: "indigo accent-3",
          RouterName: "/AddNewProducts",
        },
        {
          link: "المنتجات",
          icon: "mdi-basket",
          class: "yellow darken-4",
          RouterName: "/StoreProducts",
        },
        {
          link: "الطلبات",
          icon: "mdi-clipboard-text",
          class: "yellow darken-3",
          RouterName: "/MyOrder",
        },
        {
          link: "التقييمات",
          icon: "mdi-comment-text",
          class: "light-blue accent-4",
          RouterName: "/MyOrder",
        },
        {
          link: "رصيدي",
          icon: "mdi-wallet",
          class: "green accent-4",
          RouterName: "/StoreIncome",
        },
        // {
        //   link: "رؤى الأعمال",
        //   icon: "mdi-finance",
        //   class: "MyBusinessInsights",
        //   RouterName: "/BusinessInsights",
        // },
        // {
        //   link: "تسويق",
        //   icon: "mdi-percent-circle",
        //   class: "MyMarketingCentre",
        //   RouterName: "/Marketing",
        // },
        // {
        //   link: "المتجر الخاص بك",
        //   icon: "mdi-store-edit-outline",
        //   class: "MyStore",
        //   RouterName: "/StoreProfile",
        // },

        // {
        //   link: "إعدادات المتجر",
        //   icon: "mdi-cog-outline",
        //   class: "ShopSettings",
        //   RouterName: "/StoreProfile",
        // },
      ],
      MyStore: [
        {
          link: "رؤى الأعمال",
          icon: "mdi-chart-line",
          class: "indigo accent-2",
          RouterName: "/BusinessInsights",
        },

        {
          link: "المتجر  ",
          icon: "mdi-store-edit-outline",
          class: "pink lighten-1",
          RouterName: "/StoreProfile",
        },
        {
          link: "إعدادات ",
          icon: "mdi-cog",
          class: "grey darken-2",
          RouterName: "/StoreProfile",
        },
      ],
      FifthhAccess: [
        {
          title: " عضوية للمتجر",
          cunt: "mdi-card-account-details-star-outline ",
        },
        {
          title: "أنضم الى ثقة مول",
          cunt: "mdi-set-all ",
        },
        {
          title: " تعبئة رصيد",
          cunt: "mdi-cellphone-arrow-down mdi-rotate-180 ",
        },
        {
          title: "إعلن  لدينا ",
          cunt: "mdi-flash",
        },
        {
          title: "خدمة العملاء",
          cunt: "mdi-face-agent ",
          flib: "  transform: scaleX(-1)",
        },
      ],
      MarketingTools: [
        {
          icon: "mdi-star-circle-outline",
          title: "متميز",
          describe: "جذب انتباه المتسوقين في منتجاتك وإظهار منتجك في اول البحث",
        },
        {
          icon: "mdi-ticket-confirmation",
          title: "القسائم",
          describe:
            "زيادة الطلبات من خلال تقديم أسعار مخفضة للمشترين عند الشراء باستخدام القسائم",
        },
        {
          icon: "mdi-label-percent",
          title: "عروض الخصم",
          describe: "ضع خصومات على منتجاتك لزيادة المبيعات",
        },
        {
          icon: "mdi-handshake-outline",
          title: "صفقة الحزمة",
          describe:
            "زيادة متوسط الإنفاق لكل طلب من خلال تقديم خصومات على حزمة المنتج",
        },
        {
          icon: "mdi-basket-plus",
          title: "صفقة إضافية",
          describe:
            "بيع المزيد من المنتجات من خلال تقديم خصومات إضافية أو هدايا مجانية بحد أدنى من الشراء",
        },
        {
          icon: "mdi-home-lightning-bolt",
          title: "تخفيضات صادمة  لمتجرك ",
          describe:
            "عزز مبيعات المنتج من خلال إنشاء عروض خصم محدودة الوقت في متجرك",
        },
        {
          icon: "mdi-truck-delivery",
          title: "تخفيض في رسوم الشحن",
          describe: "قم بتعيين خصومات على رسوم الشحن لجذب المتسوقين لشراء منك",
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
  background-color: #fbe9e7;
  width: 100%;
  min-height: 100vh;
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
  font-weight: 550;
  font-size: 16px;
  color: $fontcolor !important;
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
.store-with-thiah {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  padding: 5px;
}

.link {
  font-size: 14px !important;
  letter-spacing: 0;
  color: $fontcolor !important;
  font-family: $fontfamliy3;
  display: flex;
  justify-content: center;
  //   align-items: center;
  text-align: center;
  // height: 40px;
}
.icon {
  font-size: 30px !important;
  // border-radius: 50%;
  // padding: 5px;
  // color: #fff !important;
}
.btn-noti-cart {
  color: $color-2 !important;
  // background-color: #eee;
  @media (max-width: 600px) {
  }
}
::v-deep .theme--light.v-badge .v-badge__badge:after {
  border-width: 0;
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
  border: none;
  // font-size: 13px !important;
  @media (max-width: 600px) {
    font-size: 11px !important;
  }
}
</style>
