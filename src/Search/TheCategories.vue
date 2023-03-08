<template>
  <v-tabs
    hide-slider
    show-arrows
    disabled
    grow
    class="rounded-0"
    background-color="grey lighten-3"
    active-class="transparent grey--text text--darken-1"
    center-active
  >
    <v-menu
      class="py-0"
      open-on-click
      transition="fade-transition"
      bottom
      eager
      max-height="600px"
      min-width="600px"
      offset-y
      nudge-bottom="-3px"
      v-for="Category in Categories"
      :key="Category.tital"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-tab readonly v-bind="attrs" v-on="on">
          {{ Category.tital }}
        </v-tab>
      </template>
      <v-sheet color="white" tile outlined max-width="100%" width="100%">
        <v-card-actions class="justify-space-between align-start">
          <v-list>
            <v-card-title class="pa-0">
              {{ Category.TitalForMen }}
              {{ Category.Makeup }}
              {{ Category.HomeKitchen }}
            </v-card-title>
            <v-list-item-title
              v-for="(type, x) in Category.elements"
              :key="x"
              class="title-link"
            >
              <span class="">{{ x + 1 }}</span> - {{ type.title }}
            </v-list-item-title>
          </v-list>

          <v-divider
            vertical
            class="mx-2"
            v-if="Category.elements2"
          ></v-divider>
          <v-list>
            <v-card-title class="pa-0">
              {{ Category.TitalForWomen }}
              {{ Category.HairCare }}
              {{ Category.OFFICEPRODUCTS }}
            </v-card-title>
            <v-list-item-title
              v-for="(type, x) in Category.elements2"
              :key="x"
              class="title-link"
            >
              <span class="">{{ x + 1 }}</span> - {{ type.title }}
            </v-list-item-title>
          </v-list>
          <v-divider
            vertical
            class="mx-2"
            v-if="Category.elements3"
          ></v-divider>
          <v-list>
            <v-card-title class="pa-0">
              {{ Category.TitalForKids }}
              {{ Category.BodyCare }}
              {{ Category.HomeKichLARGEAPPLIANCESine }}
            </v-card-title>
            <v-list-item-title
              v-for="(type, x) in Category.elements3"
              :key="x"
              class="title-link"
            >
              <span class="">{{ x + 1 }}</span> - {{ type.title }}
            </v-list-item-title>
          </v-list>
          <v-divider
            vertical
            class="mx-2"
            v-if="Category.elements4"
          ></v-divider>
          <v-list v-if="Category.elements4">
            <v-card-title class="pa-0">
              {{ Category.Fragrance }}
              {{ Category.SMALLAPPLIANCES }}
            </v-card-title>
            <v-list-item-title
              v-for="(type, x) in Category.elements4"
              :key="x"
              class="title-link"
            >
              <span class="">{{ x + 1 }}</span> - {{ type.title }}
            </v-list-item-title>
          </v-list>
        </v-card-actions>
      </v-sheet>
    </v-menu>
    <v-tab> اخرى</v-tab>
  </v-tabs>
</template>
<script>
export default {
  name: "TheCategories",
  components: {},
  data() {
    return {
      Categories: [
        {
          tital: "الجوالات  والأجهزة اللوحية",
          elements: [
            {
              elementId: 1393,
              title: "جوالات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أجهزة لوحية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أغطية حماية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "حماية الشاشة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "شواحن محمولة & وبطاريات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الكابلات والشواحن",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "سماعات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الساعات الذكية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " اكسسوارات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " الحواسيب",
          elements: [
            {
              elementId: 1393,
              title: "أجهزة الكمبيوتر المكتبية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " أجهزة الكمبيوتر المحمولة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملحقات الكمبيوتر ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملحقات الكمبيوتر المحمولة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " الطابعات وأجهزة العرض",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الأنترنت والشبكات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " الأزياء",
          TitalForMen: " رجالي",
          TitalForWomen: " نسائي",
          TitalForKids: " أطفالي",

          elements: [
            {
              elementId: 1393,
              title: "الملابس الداخلية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملابس خارجية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "حقائب  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أحذية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " بناطيل",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " أطقم",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "قمصان",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملابس النوم والبجامات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الجوارب",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " بدلات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " فنايل",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "بلايز",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ساعات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "نظارات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أكسسورات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements2: [
            {
              elementId: 1393,
              title: "الملابس الداخلية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملابس خارجية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس رياضية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أحذية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "حقائب نسائية ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "بلايز ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "فساتين ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ساعات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "نظارات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "أكسسورات  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "السراويل &السراويل القصيرة ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "تنانير",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس النوم والبيجامات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "عبايات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الجوارب",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس الصلاة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements3: [
            {
              elementId: 1393,
              title: "ملابس ولأدي ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس بناتي ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "حقائب أطفالي ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أحذية بناتي",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أحذية ولأدي",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: "الصحة & الجمال",
          Makeup: " مساحيق التجميل",
          HairCare: "العناية بالشعر",
          BodyCare: "العناية بالجسم",
          Fragrance: "العطور ",
          elements: [
            {
              elementId: 1393,
              title: " مكياج خافي عيوب ومصحح لون البشرة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "كريم أساس",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملمع شفاه",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "محدد شفاة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " أحمر شفاه",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " كحل",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ماسكارا",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ايشادو",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements2: [
            {
              elementId: 1393,
              title: " العناية بالشعر وفروة الرأس",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "إكسسوارات الشعر",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "شامبو & بلسم",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مجفف الشعر & وغيرها",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements3: [
            {
              elementId: 1393,
              title: "الفتمينات & مكملات غذائيه",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "المناشف   ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مكينة حلاقة رجاليه  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مكينة حلاقة نسائيه  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "صابون الجسم & كريم الترطيب &العناية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements4: [
            {
              elementId: 1393,
              title: "عطور رجالي  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "عطور نسائي ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " اثاث منزلية & مكتبية ",
          HomeKitchen: "المنزل والمطبخ",
          OFFICEPRODUCTS: " المنتجات المكتبية",
          HomeKichLARGEAPPLIANCESine: " أجهزة كبيرة",
          SMALLAPPLIANCES: " أجهزة صغيرة",
          elements: [
            {
              elementId: 1393,
              title: "الحمامات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الفراش",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ديكور المنزل",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " الأثاث المنزلي",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " المكانس والعناية بالأرضيات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " تجهيزات المطابخ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الخبز",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "السكاكين وأدوات المطبخ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "  غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements2: [
            {
              elementId: 1393,
              title: "اللوازم المكتبية والمدرسية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " أثاث مكتبي وإنارة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "التعبئة والتغليف",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements3: [
            {
              elementId: 1393,
              title: "مكيفات الهواء  ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " طباخة ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " غسالات ومجففات ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "  المراوح ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "  اجهزة التجميد ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ثلاجات ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
          elements4: [
            {
              elementId: 1393,
              title: " غلايات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "خلاط",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أفران $ التسخين",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "أفران $ التسخين",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مكنسة كهربائية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " ألعاب",
          elements: [
            {
              elementId: 1393,
              title: " بلاي ستيشن",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "اكس بوكس",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " نينتندو",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " منتجات الأطفال",
          elements: [
            {
              elementId: 1393,
              title: "لعب الأطفال والرضع",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "ملابس اطفال",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " الحمام ومستلزمات النظافة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "اللعب والتعليم",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "صحة الأطفال والعناية بالبشرة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الحليب والطعام",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " معدات الاطفال",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: "البقالة",
          elements: [
            {
              elementId: 1393,
              title: " شاى & قهوة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "المشروبات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "منتجات الالبان",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "المخبوزات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "اللوازم المنزلية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الوجبات السريعة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "المواد الغذائية الأساسية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الأغذية المعلبة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "البهارات & الأعشاب",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " لوازم الخبز والحلويات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الحبوب",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "شكلاته & حلويات ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " القرطاسية ",
          elements: [
            {
              elementId: 1393,
              title: " الكتب & المجلات & الدفاتر",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الرسم وملحقاتها",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مستلزمات مدرسية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مستلزمات مكتبيه",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مستلزمات هندسية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "مستلزمات طبية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " البناء والكهرباء",
          elements: [
            {
              elementId: 1393,
              title: " الكهرباء وملحقاتها ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " البناء وملحقاتها ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " السباكة وملحقاتها ",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " المركبات",
          elements: [
            {
              elementId: 1393,
              title: " السيارات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملحقات السيار",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },

            {
              elementId: 1393,
              title: "الشاحنات والمعدات الثقيلة",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الدراجات النارية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "الدراجات الهوائية",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " ملحقات الدراجات",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
        },
        {
          tital: " عقارات",
          elements: [
            {
              elementId: 1393,
              title: "الأراضي",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " العماير",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: " الفلل",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
            {
              elementId: 1393,
              title: "غير ذالك",
              mls: "November 2016: abc123",
              owner: "John Doe",
              expires: "2017-11-01 05:00:00",
            },
          ],
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
  },
  computed: {
    filteredStore: function () {
      return this.CarData.filter((CarData) => {
        return CarData.name.match(this.search);
      });
    },
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1);
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
.v-tabs {
  font-family: $fontfamliy2;

  .v-tab {
    letter-spacing: 0 !important;
    font-weight: 700;
  }
}
::v-deep.theme--light.v-tabs > .v-tabs-bar .v-tab:not(.v-tab--active) {
  color: $fontcolorlinks;
}
.active {
  color: $color-2 !important;
  opacity: 1;
}
::v-deep .theme--light.v-tabs .v-tab--active:focus:before {
  opacity: 0;
}
::v-deep .v-slide-group__next {
  align-items: center;
  display: flex;
  flex: 0 1 30px;
  justify-content: center;
  min-width: 30px;
  border-width: 0px 2px 0 0px;
  border-color: rgba(255, 255, 255, 0.521);
  border-style: solid;
}
::v-deep .v-slide-group__prev {
  align-items: center;
  display: flex;
  flex: 0 1 30px;
  justify-content: center;
  min-width: 30px;
  border-width: 0px 0px 0 2px;
  border-color: rgba(255, 255, 255, 0.521);
  border-style: solid;
}
::v-deep i.v-icon.notranslate.material-icons.theme--light {
  color: $color-2;
  font-size: 25px;
  font-weight: 600;
}
.title-link {
  font-family: $fontfamliy3;
  padding: 2px;
  font-weight: 500;
  cursor: pointer;
  color: rgb(128, 128, 128);
  font-size: 14px;
}
.title-link:hover {
  color: $color-2;
}
::v-deep.v-card__title.pa-0 {
  font-family: $fontfamliy;
  font-weight: 500;
  font-size: 14px;
  color: $fontcolor;
  // border-bottom: 1px solid #0000001f;
}
::v-deep.v-list.v-sheet.theme--light {
  flex-basis: 30%;
  // border-bottom: 1px solid #0000001f;
}
::v-deep.v-menu__content.theme--light.menuable__content__active {
  z-index: 50 !important;
  border-top: 3px solid $color-2;
}
</style>
