<template>
  <div class="footer hidden-sm-and-down">
    <v-footer class="" padless color="grey darken-3">
      <v-container fluid>
        <v-sheet color="transparent" class="">
          <v-row class="justify-center">
            <v-col cols="12">
              <v-sheet color="transparent">
                <v-img
                  contain
                  max-height="100"
                  class="mx-auto"
                  style="height: 110px; width: 170px"
                  src="../assets/CarLogo/Kia.png"
                  lazy-src="../assets/CarLogo/Kia.png"
                  alt="../assets/CarLogo/Kia.png"
                >
                </v-img>
                <v-subheader class="trust-text grey--text justify-center">
                  ثقتكم هي أولويتنا
                </v-subheader>
              </v-sheet>
            </v-col>
            <v-col cols="12">
              <v-card-text class="grey--text brand-text pb-2 pt-0">
                إذا كنت تحتاج إلى عدد أكبر من الفقرات يتيح لك مولد النص العربى
                زيادة عدد الفقرات كما تريد، النص لن يبدو مقسما ولا يحوي أخطاء
                لغوية، مولد النص العربى مفيد لمصممي المواقع على وجه الخصوص، حيث
                يحتاج العميل فى كثير من الأحيان أن يطلع على صورة حقيقية لتصميم
                الموقع. ومن هنا وجب على المصمم أن يضع نصوصا مؤقتة على التصميم
                ليظهر للعميل الشكل كاملاً،دور مولد النص العربى أن يوفر على
                المصمم عناء البحث عن نص بديل لا علاقة له بالموضوع الذى يتحدث عنه
                التصميم فيظهر بشكل لا يليق.
              </v-card-text>
              <v-card-actions class="justify-space-around align-start">
                <ul>
                  <v-card-subtitle class="pa-1 mb-2 pb-2 link-list-titel">
                    أولويتنا
                  </v-card-subtitle>
                  <li class="link-list" v-for="i in 3" :key="i">
                    <a> ثقتكم هي أولويتنا </a>
                  </li>
                </ul>
                <ul>
                  <v-card-subtitle class="pa-1 mb-2 pb-2 link-list-titel">
                    أولويتنا
                  </v-card-subtitle>
                  <li class="link-list" v-for="i in 3" :key="i">
                    <a> ثقتكم هي أولويتنا </a>
                  </li>
                </ul>
                <ul>
                  <v-card-subtitle class="pa-1 mb-2 pb-2 link-list-titel">
                    أولويتنا
                  </v-card-subtitle>
                  <li class="link-list" v-for="i in 3" :key="i">
                    <a> ثقتكم هي أولويتنا </a>
                  </li>
                </ul>
              </v-card-actions>
            </v-col>
            <v-col cols="12">
              <v-card flat class="grey lighten-2">
                <v-card-text class="text-center pa-2">
                  <v-btn v-for="icon in icons" :key="icon" class="mx-4" icon>
                    <v-icon size="24px">
                      {{ icon }}
                    </v-icon>
                  </v-btn>
                </v-card-text>
                <v-card-actions class="justify-space-around align-center">
                  <span class="recive-offer grey--text">
                    تلقى جميع العروض والأخبار
                  </span>
                  <v-card class="overflow-hidden pa-1" width="280px">
                    <v-text-field
                      dense
                      hide-details
                      append-icon="mdi-email"
                    ></v-text-field>
                  </v-card>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-sheet>
      </v-container>
      <v-bottom-navigation
        :value="value"
        class="align-center elevation-0 grey lighten-2"
        grow
      >
        <v-btn
          :to="{
            name: 'ThePrivacy',
            params: { Privacy: ' سياسة الخصوصية' },
          }"
          class="brand-Privacy"
        >
          سياسة الخصوصية
          <v-icon class="mb-1">mdi-alert-circle-outline</v-icon>
        </v-btn>
        <v-btn
          :to="{
            name: 'TheTerms',
            params: { Terms: ' الأحكام والشروط' },
          }"
          class="brand-Privacy"
        >
          الأحكام والشروط
          <v-icon class="mb-1">mdi-book-search-outline</v-icon>
        </v-btn>
        <v-spacer></v-spacer>
        <div class="grey--text mx-5 text-end brand-logo text--darken-1">
          <strong class="ml-2">
            &COPY; جميع الحقوق محفوظة لشركة ثـقـــة
          </strong>
          2022 —
          {{ new Date().getFullYear() }}
        </div>
      </v-bottom-navigation>
    </v-footer>
    <!-- <v-row class="py-3" no-gutters fill-height justify="center" align="center">
      <h3 class="logo-text">ثــــقـــة لتجارة الأكترونية</h3>
      <v-icon
        style="background-color: #eee; padding: 4px; border-radius: 50%"
        left
        color="#fc624d"
        size="22"
        >mdi-shopping</v-icon
      >
    </v-row> -->
  </div>
</template>
<script>
const components = {};
export default {
  name: "Footer",
  components,
  data: () => ({
    selectedItem: 1,
    items: [
      { text: " الرئيسية", path: "/" },
      { text: " تواصل معنا", path: "/contact" },
      { text: "أفتح معرضك", path: "/AboutShowroom" },
      { text: "بيع سيارتك", path: "/AboutSellingCarFreeAdd" },
      // { text: "خلي أعلان سيارتك علينا", path: "/AboutSellingCarPayAdd" },
    ],
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
  }),
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.footer {
  position: relative;
  @media (max-width: 960px) {
    background-color: $color-2;
  }
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
}
.brand-logo {
  letter-spacing: 0px;
  font-family: $fontfamliy3;
  font-size: 16px;
  font-weight: 300;
}
.brand-text {
  letter-spacing: 0px;
  font-family: $fontfamliy;
  font-size: 15px;
  font-weight: 400;
  line-height: 1.6;
  text-align: justify;
}
.trust-text {
  letter-spacing: 0px;
  font-family: $fontfamliy3;
  font-size: 20px;
  font-weight: bold;
}
.recive-offer {
  letter-spacing: 0px;
  font-family: $fontfamliy3;
  font-size: 17px !important;
  font-weight: bold !important;
}
.brand-Privacy {
  letter-spacing: 0px;
  font-family: $fontfamliy3;
  font-size: 16px;
  font-weight: 600;
}
::v-deep .v-slide-group__content.v-tabs-bar__content {
  justify-content: center;
}
.link-list {
  letter-spacing: 0px;
  list-style-type: none;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  margin: 3px 0;
  font-size: 14px !important;
  a {
    text-decoration: none;
  }
}
.link-list-titel {
  letter-spacing: 0px;
  list-style-type: none;
  color: $fontcolorlinks;
  font-family: $fontfamliy3;
  font-size: 17px !important;
  border-bottom: 2px solid rgb(209, 209, 209);
}
</style>
