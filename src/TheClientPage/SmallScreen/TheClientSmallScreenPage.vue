<template>
  <div class="client-store">
    <!-- client Card -->
    <v-card
      style="background: linear-gradient(180deg, #eeeeee 0%, #FFE0B2 100%)"
      flat
      class="mx-auto grey"
      tile
    >
      <v-container>
        <!-- client Card -->
        <v-row align="center" no-gutters class="fill-height">
          <v-avatar class="profile" color="grey" size="50">
            <v-img
              src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
            ></v-img>
          </v-avatar>
          <v-col cols="7" md="10" sm="9" lg="10">
            <v-list-item color="grey">
              <v-list-item-content>
                <v-list-item-title class="user-name">
                  محمد أمين شمسان
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-row justify="end" no-gutters>
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
                icon
              >
                <v-icon> mdi-bell-outline </v-icon>
              </v-btn>
            </v-badge>
            <v-btn depressed width="36" height="36" icon class="btn-noti-cart">
              <v-icon>mdi-dots-vertical </v-icon>
            </v-btn>
          </v-row>
        </v-row>
        <!-- quick information  -->
        <v-row align="center" no-gutters class="fill-height mt-6">
          <v-col v-for="(First, i) in FirstAccess" :key="i">
            <v-card color="transparent" flat tile>
              <v-card-text class="pa-0 text-No text-center">
                {{ First.cunt }}
              </v-card-text>
              <v-card-text class="pa-0 mt-1 text text-center">
                {{ First.title }}
              </v-card-text>
            </v-card>
          </v-col>
          <v-col>
            <v-card
              link
              router
              :to="{
                name: 'SmallScreenClientCouponsPage',
                params: { coupons: 'قسائم' },
              }"
              color="transparent"
              flat
              tile
            >
              <v-card-text class="pa-0 text-No text-center"> 8 </v-card-text>
              <v-card-text class="pa-0 mt-1 text text-center">
                القسائم
              </v-card-text>
            </v-card>
          </v-col>
          <v-col>
            <v-card
              link
              router
              :to="{
                name: 'SmallScreenClientPointsPage',
                params: { Points: 'نقاط' },
              }"
              color="transparent"
              flat
              tile
            >
              <v-card-text class="pa-0 text-No text-center"> 8 </v-card-text>
              <v-card-text class="pa-0 mt-1 text text-center">
                النقاط
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
    <v-container class="py-0">
      <!-- order  -->
      <v-card flat rounded="lg" class="pa-2 mt-0 mb-3">
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
                >
                  {{ Second.cunt }}
                </v-icon>
              </v-row>
              <v-card-text
                style="height: 45px"
                class="pa-0 mt-2 text text-center"
              >
                {{ Second.title }}
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- row for cart and other  -->
      <v-card rounded="lg" flat class="pa-2 my-3">
        <v-row align="center" no-gutters class="fill-height">
          <!-- cart btn  -->
          <v-col class="px-1">
            <v-card
              flat
              :to="{
                name: 'SmallScreenClientCartPage',
                params: { Cart: 'مشترياتي' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon color="#fc624d" size="27"> mdi-cart-outline </v-icon>
              </v-row>
              <v-card-text class="pa-0 mt-2 text text-center">
                سلة التسوق
              </v-card-text>
            </v-card>
          </v-col>
          <!-- thiqah mall btn  -->
          <v-col class="px-1">
            <v-card
              flat
              :to="{
                name: 'SmallScreenShare',
                params: { Share: 'شارك وأربح' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon
                  style="border-radius: 50%"
                  color="deep-orange darken-2"
                  size="27"
                >
                  mdi-shopping
                </v-icon>
              </v-row>
              <v-card-text class="pa-0 mt-2 text text-center">
                ثقة مول
              </v-card-text>
            </v-card>
          </v-col>
          <!-- share and wain btn  -->
          <v-col class="px-1">
            <v-card
              flat
              :to="{
                name: 'SmallScreenShare',
                params: { Share: 'شارك وأربح' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon color="blue-grey darken-1" size="27">
                  mdi-link-box
                </v-icon>
              </v-row>
              <v-card-text class="pa-0 mt-2 text text-center">
                شارك وأربح
              </v-card-text>
            </v-card>
          </v-col>
          <!-- open your store btn  -->
          <v-col class="px-1">
            <v-card
              flat
              :to="{
                name: 'SmallScreenShare',
                params: { Share: 'شارك وأربح' },
              }"
            >
              <v-row justify="center" no-gutters class="fill-height">
                <v-icon color="blue-grey darken-1" size="27">
                  mdi-file-sign
                </v-icon>
              </v-row>
              <v-card-text class="pa-0 mt-2 text text-center">
                ابدأ في البيع
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-card>
      <!-- wallet  -->
      <v-card rounded="lg" flat class="pa-2 my-3">
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
      <!-- comment help last-seen .....  -->
      <v-card rounded="lg" flat class="pa-2 my-3">
        <v-row align="center" no-gutters class="fill-height mb-5">
          <v-col class="px-1" v-for="(Fift, i) in FifthhAccess" :key="i">
            <v-row justify="center" no-gutters class="fill-height">
              <v-icon :style="Fift.flib" color="grey darken-2" size="27">
                {{ Fift.cunt }}
              </v-icon>
            </v-row>
            <v-card-text class="pa-0 mt-1 text text-center"
              >{{ Fift.title }}
            </v-card-text>
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
              >
                {{ Sixth.cunt }}
              </v-icon>
            </v-row>
            <v-card-text class="pa-0 mt-1 text text-center">
              {{ Sixth.title }}
            </v-card-text>
          </v-col>
        </v-row>
      </v-card>
      <!-- follow  -->
      <v-card flat rounded="lg" class="my-2 pa-2" min-height="200">
        <v-card-text class="pt-2 card-titel">متابع </v-card-text>
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
      </v-card>
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
  background-color: #FFF3E0;
  width: 100%;
  min-height: 100vh;
  @media (max-width: 960px) {
    margin-bottom: 49px;
  }
}
.v-list-item__title.text.text-h6 {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
}
.user-name {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  font-size: 16px !important;
  line-height: 1.7 !important;
}
.text {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  font-size: 13px !important;
}
.text-No {
  font-weight: 600;
  font-size: 16px !important;
  font-family: sans-serif !important;
}
.card-titel {
  letter-spacing: 0 !important;
  font-family: $fontfamliy3 !important;
  font-weight: 600;
  font-size: 17px;
  @media (max-width: 450px) {
    font-size: 15px;
  }
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
