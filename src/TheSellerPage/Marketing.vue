<template>
  <div class="Marketing">
    <!-- small Screen Tabs  -->
    <div class="hidden-md-and-up">
      <v-app-bar flat fixed color="#fc624d" dark>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-home </v-icon>
        </v-btn>
        <v-toolbar-title class="pr-1 titel">الرئيسية</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn
          :to="{
            name: 'MainStorePage',
            params: { MyCar: 'إعلاناتي' },
          }"
          icon
        >
          <v-icon> mdi-arrow-left </v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet height="56"></v-sheet>
    </div>
    <!-- events  -->
    <v-sheet rounded="lg" class="">
      <v-card-title class="welcom-text"> المنسبات </v-card-title>
      <!-- new events  -->
      <div>
        <v-card-subtitle> منسبات جديد </v-card-subtitle>
        <v-row no-gutters>
          <v-col>events</v-col>
          <v-col>events</v-col>
        </v-row>
      </div>
      <!-- Thiqh events  -->
      <div>
        <v-card-subtitle class="text">
          انضم إلى أحداث ثـقـة الرسمي
        </v-card-subtitle>
        <v-row align="center" no-gutters>
          <v-col class="pa-2" md="6" lg="6" sm="6" cols="6">
            <v-hover v-slot="{ hover }">
              <v-card
                color="#FAFAFA"
                :elevation="hover ? 3 : 0"
                class="mx-auto"
              >
                <v-row align="center" no-gutters>
                  <v-col>
                    <v-avatar class="profile" color="transparent" size="70">
                      <v-img
                        src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                      ></v-img>
                    </v-avatar>
                  </v-col>
                  <v-col cols="9">
                    <v-card-title class="pa-0 text">
                      حملة المنتجات
                    </v-card-title>
                    <v-card-subtitle
                      class="pa-0 pt-3 grey--text text--darken-1"
                    >
                      انضم إلى حملات ثـقـة الرسمية للوصول إلى المزيد من
                      المتسوقين
                    </v-card-subtitle>
                  </v-col>
                </v-row>
              </v-card>
            </v-hover>
          </v-col>
          <v-col class="pa-2" md="6" lg="6" sm="6" cols="12">
            <v-hover v-slot="{ hover }">
              <v-card
                color="#FAFAFA"
                :elevation="hover ? 3 : 0"
                class="mx-auto"
              >
                <v-row align="center" no-gutters>
                  <v-col>
                    <v-avatar class="profile" color="transparent" size="70">
                      <v-img
                        src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"
                      ></v-img>
                    </v-avatar>
                  </v-col>
                  <v-col cols="9">
                    <v-card-title class="pa-0 text">
                      حملة المنتجات
                    </v-card-title>
                    <v-card-subtitle
                      class="pa-0 pt-3 grey--text text--darken-1"
                    >
                      انضم إلى حملات ثـقـة الرسمية للوصول إلى المزيد من
                      المتسوقين
                    </v-card-subtitle>
                  </v-col>
                </v-row>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </div>
    </v-sheet>
    <!-- Marketing Tools  -->
    <v-sheet rounded="lg" class="my-2">
      <v-card-title class="welcom-text"> أدوات التسويق </v-card-title>
      <div>
        <v-card-subtitle>زيادة مبيعاتك من خلال الترويج</v-card-subtitle>
        <v-row no-gutters>
          <v-col
            class="pa-2"
            md="4"
            lg="4"
            sm="6"
            cols="12"
            v-for="(Tool, i) in MarketingTools"
            :key="i"
          >
            <v-hover v-slot="{ hover }">
              <v-card
                color="#FAFAFA"
                :elevation="hover ? 3 : 0"
                class="mx-auto"
                height="100%"
              >
                <v-row class="fill-height" align="center" no-gutters>
                  <v-col class="text-center">
                    <v-avatar
                      class="profile"
                      color="light-blue lighten-5"
                      size="50"
                    >
                      <v-icon size="30" color="light-blue  ">
                        {{ Tool.icon }}
                      </v-icon>
                    </v-avatar>
                  </v-col>
                  <v-col cols="9">
                    <v-card-title class="pa-0 text">
                      {{ Tool.title }}
                    </v-card-title>
                    <v-card-subtitle
                      style="font-size: 13px"
                      class="pa-0 pt-3 grey--text text--darken-1"
                    >
                      {{ Tool.describe }}
                    </v-card-subtitle>
                  </v-col>
                </v-row>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </div>
      <!-- Engage with Your Shoppers  -->
      <div>
        <v-card-subtitle> كن أقرب للمتسوقين</v-card-subtitle>
        <v-row no-gutters>
          <v-col
            class="pa-2"
            md="4"
            lg="4"
            sm="6"
            cols="12"
            v-for="(Shoppers, i) in EngageShoppers"
            :key="i"
          >
            <v-hover v-slot="{ hover }">
              <v-card
                color="#FAFAFA"
                :elevation="hover ? 3 : 0"
                class="mx-auto"
                height="100%"
              >
                <v-row class="fill-height" align="center" no-gutters>
                  <v-col class="text-center">
                    <v-avatar class="profile" color="teal lighten-5" size="50">
                      <v-icon size="30" color="teal">
                        {{ Shoppers.icon }}
                      </v-icon>
                    </v-avatar>
                  </v-col>
                  <v-col cols="9">
                    <v-card-title class="pa-0 text">
                      {{ Shoppers.title }}
                    </v-card-title>
                    <v-card-subtitle
                      style="font-size: 13px"
                      class="pa-0 pt-3 grey--text text--darken-1"
                    >
                      {{ Shoppers.describe }}
                    </v-card-subtitle>
                  </v-col>
                </v-row>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </div>
      <!--  Increase Your Shop customer  -->
      <div>
        <v-card-subtitle>
          زيادة حركة الزوار على متجرك أو منتجاتك
        </v-card-subtitle>
        <v-row no-gutters>
          <v-col
            class="pa-2"
            md="4"
            lg="4"
            sm="6"
            cols="12"
            v-for="(Customer, i) in IncreaseCustomer"
            :key="i"
          >
            <v-hover v-slot="{ hover }">
              <v-card
                color="#FAFAFA"
                :elevation="hover ? 3 : 0"
                class="mx-auto"
                height="100%"
              >
                <v-row class="fill-height" align="center" no-gutters>
                  <v-col class="text-center">
                    <v-avatar
                      class="profile"
                      color="orange  lighten-5"
                      size="50"
                    >
                      <v-icon size="30" color="orange   ">
                        {{ Customer.icon }}
                      </v-icon>
                    </v-avatar>
                  </v-col>
                  <v-col cols="9">
                    <v-card-title class="pa-0 text">
                      {{ Customer.title }}
                    </v-card-title>
                    <v-card-subtitle
                      style="font-size: 13px"
                      class="pa-0 pt-3 grey--text text--darken-1"
                    >
                      {{ Customer.describe }}
                    </v-card-subtitle>
                  </v-col>
                </v-row>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </div>
    </v-sheet>
  </div>
</template>
<script>
export default {
  name: "Marketing",
  data() {
    return {
      MarketingTools: [
        {
          icon: "mdi-star-circle-outline",
          title: "متميز",
          describe:
            "جذب انتباه المتسوقين في منتجاتك وإظهار منتجك في اول البحث",
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
      EngageShoppers: [
        {
          icon: "mdi-gift",
          title: "متابعة  + جائزة",
          describe:
            "شجع المتسوقين على متابعة متجرك بمكافأة قسائم المتابعين الجدد",
        },
        {
          icon: "mdi-comment-check",
          title: " تقييم + الجائزة",
          describe: "اجذب العملاء لترك تقييمات أفضل من خلال مكافأة عملات ثقة .",
        },
      ],
      IncreaseCustomer: [
        {
          icon: "mdi-store",
          title: "أنضم مع ثقة مول ",
          describe:
            "زيادة المبيعات والزوار من خلال عرض منتجاتك ومتجرك بطاب  ثقة مول وترخيص متجرك",
        },
      ],
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
    decrement() {
      this.offer--;
    },
    increment() {
      this.offer++;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Marketing {
  width: 100%;
  min-height: 100vh;
  font-family: $fontfamliy3 !important;

  .welcom-text {
    font-family: $fontfamliy3;
    color: grey;
    letter-spacing: 0px;
    @media (max-width: 800px) {
      font-size: 17px;
    }
  }
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  font-family: $fontfamliy3;
  font-weight: 600;
  font-size: 14px;
  // height: 18px;
  color: $fontcolorlinks;
  text-align: center;
}
::v-deep .v-dialog.v-dialog--active.v-dialog--persistent {
  margin: 5px;
}
.detail {
  font-family: $fontfamliy3;
  font-weight: 600;
  font-size: 15px !important;
}
.price {
  font-family: sans-serif !important;
  font-weight: 700 !important;
  font-size: 19px !important;
  display: flex;
  color: $color-2 !important;
  span {
    font-size: 13px !important;
    margin-right: 2px;
  }
}
.btn {
  font-family: $fontfamliy3;
  font-weight: 500;
  font-size: 15px !important;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
}
.stocked {
  font-family: sans-serif;
  font-size: 16px;
  font-weight: 700;
}

.cat {
  font-family: $fontfamliy3;
  font-weight: 500;
  font-size: 13px !important;
  @media (max-width: 600px) {
    font-size: 13px !important;
    padding: 10px !important;
  }
}
.disc-text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px;
  padding: 5px;
  display: block;
  text-align: center;
}
.chip {
  // border-color: $color-2 !important;
  font-size: 14px !important;
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  color: $fontcolorlinks !important;
  // font-weight: 600;
}
.text {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 17px !important;
}
.btn {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  color: $fontcolor !important;
  font-size: 14px !important;
  font-weight: 600 !important;
  padding: 0 6px !important ;
  min-width: 50px !important;
}
.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
</style>
