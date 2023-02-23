<template>
  <div class="ShowRoomAddNewCar">
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
    <v-container class="pa-0">
      <!-- Add the the images  -->
      <v-sheet rounded="lg" class="pa-2 ma-2">
        <v-row no-gutters class="pa-0">
          <v-col class="pa-1" cols="4" sm="4" md="2" lg="2">
            <v-card class="">
              <div class="image-preview ma-1">
                <div v-if="imageData.length <= 0">
                  <v-icon> mdi-plus </v-icon>
                </div>
                <div class="preview" v-if="imageData.length > 0">
                  <img :src="imageData" />
                </div>
                <label class="cover-image-input" for="file"></label>
                <v-btn
                  v-if="imageData.length > 0"
                  icon
                  small
                  class="btn"
                  @click="imageData = ''"
                >
                  <v-icon> mdi-close </v-icon>
                </v-btn>
                <input
                  @change="previewImage"
                  accept="image/*"
                  type="file"
                  id="file"
                  class="custom-file-input"
                />
              </div>
              <span class="photo-text">صورة الغلاف</span>
            </v-card>
          </v-col>
          <v-col
            class="pa-1"
            cols="4"
            sm="4"
            md="2"
            lg="2"
            v-for="(imag, i) in 2"
            :key="i"
          >
            <v-card class="">
              <div class="image-preview ma-1">
                <div v-if="imageData.length <= 0">
                  <v-icon> mdi-plus </v-icon>
                </div>
                <div class="preview" v-if="imageData.length > 0">
                  <img :src="imageData" />
                </div>
                <label class="cover-image-input" for="file"></label>
                <v-btn
                  v-if="imageData.length > 0"
                  icon
                  small
                  class="btn"
                  @click="imageData = ''"
                >
                  <v-icon> mdi-close </v-icon>
                </v-btn>
                <input
                  @change="previewImage"
                  accept="image/*"
                  type="file"
                  id="file"
                  class="custom-file-input"
                />
              </div>
              <span class="photo-text">صورة {{ i + 1 }}</span>
            </v-card>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- fill the goods name -->
      <v-sheet rounded="lg" class="ma-2 py-2">
        <div>
          <v-card-title class="add-text pa-0 mx-2">
            أسم المنتج
            <span class="red--text">*</span>
            <v-spacer></v-spacer>
            <div>
              <span class="text-cunt">
                {{ ProductName.length }}
                / 120
              </span>
            </div>
          </v-card-title>
          <v-text-field
            solo
            flat
            dense
            placeholder="إدخل أسم المنتج"
            class="ma-0 pa-0"
            hide-details
            v-model="ProductName"
          ></v-text-field>
        </div>
      </v-sheet>
      <!-- fill the goods description   -->
      <v-sheet rounded="lg" class="ma-2 py-2">
        <div>
          <v-card-title class="add-text pa-0 mx-2">
            وصف المنتج
            <span class="red--text">*</span>
            <v-spacer></v-spacer>
            <div>
              <span class="text-cunt">
                {{ ProductDescription.length }}
                / 3000
              </span>
            </div>
          </v-card-title>
          <v-textarea
            solo
            flat
            dense
            placeholder="إدخل وصف المنتج"
            class="ma-0 pa-0"
            hide-details
            v-model="ProductDescription"
            rows="5"
          ></v-textarea>
        </div>
      </v-sheet>
      <!-- categories Big Screen   -->
      <v-sheet rounded="lg" class="ma-2 py-2">
        <v-card-title class="add-text pa-2">
          فئة المنتج
          <span class="red--text ml-1">*</span>
        </v-card-title>
        <v-row no-gutters>
          <v-col class="px-2" cols="12" md="4" lg="4">
            <v-sheet
              class="overflow-y-auto"
              color="grey lighten-3"
              height="200"
            >
              <v-chip-group active-class="blue white--text" column>
                <v-chip
                  text-color="black"
                  @click.stop="CategoryOne = !CategoryOne"
                  v-text="item.title"
                  v-for="item in Categories"
                  :key="item.id"
                >
                </v-chip>
              </v-chip-group>
            </v-sheet>
          </v-col>
          <v-col class="px-2" cols="12" md="4" lg="4" v-if="CategoryOne">
            <v-sheet
              color="grey lighten-3"
              class="overflow-y-auto"
              height="200"
            >
              <v-chip-group active-class="blue white--text" column>
                <v-chip
                  @click.stop="NameAndNumber = !NameAndNumber"
                  text-color="black"
                  v-text="item.title"
                  v-for="item in Categories"
                  :key="item.id"
                >
                </v-chip>
              </v-chip-group>
            </v-sheet>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- variation Big Screen   -->
      <v-sheet rounded="lg" class="ma-2 py-2">
        <v-card-title class="add-text pa-2">
          تفاوت
          <span class="red--text ml-1">*</span>
          <v-spacer></v-spacer>
          <v-btn color="blue" class="text" text>تعديل</v-btn>
        </v-card-title>
        <v-row no-gutters>
          <!-- Color or Edit  -->
          <v-col class="pa-1" cols="12" md="4" lg="4">
            <v-sheet
              class="overflow-y-auto"
              color="grey lighten-3"
              min-height="200"
            >
              <v-row no-gutters class="pa-1">
                <span class="text mr-2"> الألوان </span>
                <v-spacer></v-spacer>
                <v-btn color="blue" class="text" text>تعديل</v-btn>
              </v-row>
              <v-divider></v-divider>
              <v-row no-gutters class="pa-2">
                <v-col class="pa-1" cols="3" v-for="i in 2" :key="i">
                  <v-card flat class="text pa-1 text-center"> الألوان </v-card>
                </v-col>
                <v-col class="pa-1" cols="3">
                  <v-card
                    color="transparent"
                    flat
                    class="text pa-1 text-center"
                  >
                    أكثر
                    <v-icon color="blue">mdi-plus</v-icon>
                  </v-card>
                </v-col>
              </v-row>
              <v-row no-gutters class="pa-2">
                <v-col class="pa-1" cols="12">
                  <v-switch
                    hide-details
                    class="ma-0"
                    v-model="switch1"
                    label="إضافة صور (للألوان)"
                  ></v-switch>
                  <v-card-subtitle style="margin-right: 44px" class="pa-0">
                    سوف يتم إظهار الصورة عند الظغط على (للألوان)
                  </v-card-subtitle>
                </v-col>
              </v-row>
              <v-row no-gutters v-if="switch1">
                <v-col class="pa-1" cols="4" v-for="(imag, i) in 2" :key="i">
                  <div class="image-pre-variation ma-1">
                    <div v-if="imageData.length <= 0">
                      <v-icon> mdi-plus </v-icon>
                    </div>
                    <div class="pre-variation" v-if="imageData.length > 0">
                      <img :src="imageData" />
                    </div>
                    <label class="cover-image-input" for="file"></label>
                    <v-btn
                      v-if="imageData.length > 0"
                      icon
                      small
                      class="btn"
                      @click="imageData = ''"
                    >
                      <v-icon> mdi-close </v-icon>
                    </v-btn>
                    <input
                      @change="previewImage"
                      accept="image/*"
                      type="file"
                      id="file"
                      class="custom-file-input"
                    />
                    <span class="text mr-2"> الألوان </span>
                  </div>
                </v-col>
              </v-row>
            </v-sheet>
          </v-col>
          <!-- Size or Edit  -->
          <v-col class="pa-1" cols="12" md="4" lg="4">
            <v-sheet
              class="overflow-y-auto"
              color="grey lighten-3"
              min-height="200"
            >
              <v-row no-gutters class="pa-1">
                <span class="text mr-2"> المقاس </span>
                <v-spacer></v-spacer>
                <v-btn color="blue" class="text" text>تعديل</v-btn>
              </v-row>
              <v-divider></v-divider>
              <v-row no-gutters class="pa-2">
                <v-col class="pa-1" cols="3" v-for="i in 2" :key="i">
                  <v-card flat class="text pa-1 text-center"> الألوان </v-card>
                </v-col>
                <v-col class="pa-1" cols="3">
                  <v-card
                    color="transparent"
                    flat
                    class="text pa-1 text-center"
                  >
                    أكثر
                    <v-icon color="blue">mdi-plus</v-icon>
                  </v-card>
                </v-col>
              </v-row>
            </v-sheet>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- set price individually Big Screen   -->
      <v-sheet rounded="lg" class="ma-2 py-2">
        <v-card-title class="add-text pa-2">
          تحديد السعر بشكل فردي
          <span class="red--text ml-1">*</span>
          <v-spacer></v-spacer>
        </v-card-title>
        <v-row
          style="border-bottom: 1px solid #eee"
          align="center"
          class="pa-2 grey lighten-4"
          no-gutters
        >
          <v-col class="px-2 text-center">النوع</v-col>
          <v-col class="px-2 text-center"> السعر </v-col>
          <v-col class="px-2 text-center"> مخزون </v-col>
        </v-row>
        <v-row
          style="border-bottom: 1px solid #eee"
          align="center"
          class="pa-2"
          no-gutters
        >
          <v-col>اسود</v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="ريال"
            ></v-text-field>
          </v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="قطعة"
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row
          style="border-bottom: 1px solid #eee"
          align="center"
          class="pa-2"
          no-gutters
        >
          <v-col>اسود</v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="ريال"
            ></v-text-field>
          </v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="قطعة"
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row align="center" class="pa-2" no-gutters>
          <v-col>اسود</v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="ريال"
            ></v-text-field>
          </v-col>
          <v-col class="px-2">
            <v-text-field
              outlined
              hide-details
              dense
              type="number"
              suffix="قطعة"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-sheet>
      <v-sheet rounded="lg" class="ma-2 py-2">
        <v-card-title class="add-text pa-2">
          تحديد السعر والمخزون للجميع
          <span class="red--text ml-1">*</span>
          <v-spacer></v-spacer>
        </v-card-title>
        <v-row
          style="border-bottom: 1px solid #eee"
          align="center"
          class="pa-2"
          no-gutters
        >
          <v-col md="6" lg="6" sm="6" cols="12" class="pa-2">
            <v-text-field
              outlined
              hide-details
              dense
              placeholder="ريال السعر ( 99999.99 ~ 0.10 )"
              type="number"
              suffix="ريال"
            ></v-text-field>
          </v-col>
          <v-col md="6" lg="6" sm="6" cols="12" class="pa-2">
            <v-text-field
              outlined
              hide-details
              placeholder="المخزون ( 10000 ~ 1 )"
              dense
              type="number"
              suffix="قطعة"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-sheet>
      <!-- Save Or cancel -->
      <v-card-actions class="justify-center pa-4" v-if="step === 3">
        <v-btn
          width="200"
          depressed
          @click="step++"
          elevation="0"
          class="save-pu-btn"
        >
          احفظ وانشر
        </v-btn>
        <v-btn @click="step++" elevation="0" class="cancel-btn"> إلغاء </v-btn>
      </v-card-actions>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "ShowRoomAddNewCar",
  components: {},
  data() {
    return {
      // checkbox
      switch1: false,
      ProductName: "",
      ProductDescription: "",
      color: false,
      size: false,
      model: false,
      flavor: false,
      CategoryOne: null,
      NameAndNumber: null,
      Quantity: null,
      //
      items: ["foo", "bar", "fizz", "buzz"],
      value: ["foo", "bar", "fizz", "buzz"],
      step: 1,
      imageData: "",
      Categories: [
        {
          title: "الجوالات  والأجهزة اللوحية",
          id: 1,
          // children: [
          //   {
          //     id: 2,
          //     title: "جوالات",
          //   },
          //   {
          //     id: 3,
          //     title: "أجهزة لوحية",
          //   },
          //   {
          //     id: 4,
          //     title: "أغطية حماية",
          //   },
          //   {
          //     id: 5,
          //     title: "حماية الشاشة",
          //   },
          //   {
          //     id: 6,
          //     title: "شواحن محمولة & وبطاريات",
          //   },
          //   {
          //     id: 7,
          //     title: "الكابلات والشواحن",
          //   },
          //   {
          //     id: 8,
          //     title: "سماعات",
          //   },
          //   {
          //     id: 9,
          //     title: "الساعات الذكية",
          //   },
          //   {
          //     id: 10,
          //     title: " اكسسوارات",
          //   },
          //   {
          //     id: 11,
          //     title: " غير ذالك",
          //   },
          // ],
        },
        {
          title: " الحواسيب",
          id: 12,
          // children: [
          //   {
          //     id: 13,
          //     title: "أجهزة الكمبيوتر المكتبية",
          //   },
          //   {
          //     id: 14,
          //     title: " أجهزة الكمبيوتر المحمولة",
          //   },
          //   {
          //     id: 15,
          //     title: " ملحقات الكمبيوتر ",
          //   },
          //   {
          //     id: 16,
          //     title: " ملحقات الكمبيوتر المحمولة",
          //   },
          //   {
          //     id: 17,
          //     title: " الطابعات وأجهزة العرض",
          //   },
          //   {
          //     id: 18,
          //     title: "الأنترنت والشبكات",
          //   },
          //   {
          //     id: 19,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " الأزياء",
          id: 20,
          // children: [
          //   {
          //     title: " رجالي",
          //     id: 21,
          //     children: [
          //       {
          //         id: 22,
          //         title: "الملابس الداخلية",
          //       },
          //       {
          //         id: 23,
          //         title: " ملابس خارجية",
          //       },

          //       {
          //         id: 24,
          //         title: "حقائب  ",
          //       },
          //       {
          //         id: 25,
          //         title: "أحذية",
          //       },
          //       {
          //         id: 26,
          //         title: " بناطيل",
          //       },
          //       {
          //         id: 27,
          //         title: " أطقم",
          //       },
          //       {
          //         id: 28,
          //         title: "قمصان",
          //       },
          //       {
          //         id: 29,
          //         title: " ملابس النوم والبجامات",
          //       },
          //       {
          //         id: 30,
          //         title: "الجوارب",
          //       },
          //       {
          //         id: 31,
          //         title: " بدلات",
          //       },
          //       {
          //         id: 32,
          //         title: " فنايل",
          //       },
          //       {
          //         id: 33,
          //         title: "بلايز",
          //       },
          //       {
          //         id: 34,
          //         title: "ملابس ",
          //       },
          //       {
          //         id: 35,
          //         title: "ساعات  ",
          //       },
          //       {
          //         id: 36,
          //         title: "نظارات  ",
          //       },
          //       {
          //         id: 37,
          //         title: "أكسسورات  ",
          //       },
          //       {
          //         id: 38,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: " نسائي",
          //     id: 39,
          //     children: [
          //       {
          //         id: 40,
          //         title: "الملابس الداخلية",
          //       },
          //       {
          //         id: 41,
          //         title: " ملابس خارجية",
          //       },

          //       {
          //         id: 42,
          //         title: "حقائب  ",
          //       },
          //       {
          //         id: 43,
          //         title: "أحذية",
          //       },
          //       {
          //         id: 44,
          //         title: " بناطيل",
          //       },
          //       {
          //         id: 45,
          //         title: " أطقم",
          //       },
          //       {
          //         id: 46,
          //         title: "قمصان",
          //       },
          //       {
          //         id: 47,
          //         title: " ملابس النوم والبجامات",
          //       },
          //       {
          //         id: 48,
          //         title: "الجوارب",
          //       },
          //       {
          //         id: 49,
          //         title: " بدلات",
          //       },
          //       {
          //         id: 50,
          //         title: " فنايل",
          //       },
          //       {
          //         id: 51,
          //         title: "بلايز",
          //       },
          //       {
          //         id: 52,
          //         title: "ملابس ",
          //       },
          //       {
          //         id: 53,
          //         title: "ساعات  ",
          //       },
          //       {
          //         id: 54,
          //         title: "نظارات  ",
          //       },
          //       {
          //         id: 55,
          //         title: "أكسسورات  ",
          //       },
          //       {
          //         id: 56,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: " أطفالي",
          //     id: 57,
          //     children: [
          //       {
          //         id: 58,
          //         title: "ملابس ولأدي ",
          //       },
          //       {
          //         id: 59,
          //         title: "ملابس بناتي ",
          //       },
          //       {
          //         id: 60,
          //         title: "حقائب أطفالي ",
          //       },
          //       {
          //         id: 61,
          //         title: "أحذية بناتي",
          //       },
          //       {
          //         id: 62,
          //         title: "أحذية ولأدي",
          //       },
          //       {
          //         id: 63,
          //         title: "غير ذالك ",
          //       },
          //     ],
          //   },
          // ],
        },
        {
          title: "الصحة & الجمال",
          id: 64,
          // children: [
          //   {
          //     title: " مساحيق التجميل",
          //     id: 65,
          //     children: [
          //       {
          //         id: 66,
          //         title: " مكياج خافي عيوب ومصحح لون البشرة",
          //       },
          //       {
          //         id: 67,
          //         title: "كريم أساس",
          //       },
          //       {
          //         id: 68,
          //         title: "ملمع شفاه",
          //       },
          //       {
          //         id: 69,
          //         title: "محدد شفاة",
          //       },
          //       {
          //         id: 70,
          //         title: " أحمر شفاه",
          //       },
          //       {
          //         id: 71,
          //         title: " كحل",
          //       },
          //       {
          //         id: 72,
          //         title: "ماسكارا",
          //       },
          //       {
          //         id: 73,
          //         title: "ايشادو",
          //       },
          //       {
          //         id: 74,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: "العناية بالشعر",
          //     id: 75,
          //     children: [
          //       {
          //         id: 76,
          //         title: " العناية بالشعر وفروة الرأس",
          //       },
          //       {
          //         id: 77,
          //         title: "إكسسوارات الشعر",
          //       },
          //       {
          //         id: 78,
          //         title: "شامبو & بلسم",
          //       },
          //       {
          //         id: 79,
          //         title: "مجفف الشعر & وغيرها",
          //       },
          //       {
          //         id: 80,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: "العناية بالجسم ",
          //     id: 81,
          //     children: [
          //       {
          //         id: 82,
          //         title: "الفتمينات & مكملات غذائيه",
          //       },
          //       {
          //         id: 83,
          //         title: "المناشف   ",
          //       },
          //       {
          //         id: 84,
          //         title: "مكينة حلاقة رجاليه  ",
          //       },
          //       {
          //         id: 85,
          //         title: "مكينة حلاقة نسائيه  ",
          //       },
          //       {
          //         id: 86,
          //         title: "صابون الجسم & كريم الترطيب &العناية",
          //       },
          //       {
          //         id: 87,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: "العطور",
          //     id: 88,
          //     children: [
          //       {
          //         id: 89,
          //         title: "عطور رجالي  ",
          //       },
          //       {
          //         id: 90,
          //         title: "عطور نسائي ",
          //       },
          //       {
          //         id: 91,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          // ],
        },
        {
          title: " اثاث منزلية & مكتبية ",
          id: 92,
          // children: [
          //   {
          //     title: "المنزل والمطبخ",
          //     id: 93,
          //     children: [
          //       {
          //         id: 94,
          //         title: "الحمامات",
          //       },
          //       {
          //         id: 95,
          //         title: "الفراش",
          //       },
          //       {
          //         id: 96,
          //         title: "ديكور المنزل",
          //       },
          //       {
          //         id: 97,
          //         title: " الأثاث المنزلي",
          //       },
          //       {
          //         id: 98,
          //         title: " المكانس والعناية بالأرضيات",
          //       },
          //       {
          //         id: 99,
          //         title: " تجهيزات المطابخ",
          //       },
          //       {
          //         id: 100,
          //         title: "الخبز",
          //       },
          //       {
          //         id: 101,
          //         title: "السكاكين وأدوات المطبخ",
          //       },
          //       {
          //         id: 102,
          //         title: "  غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: " المنتجات المكتبية",
          //     id: 103,
          //     children: [
          //       {
          //         id: 104,
          //         title: "اللوازم المكتبية والمدرسية",
          //       },
          //       {
          //         id: 105,
          //         title: " أثاث مكتبي وإنارة",
          //       },
          //       {
          //         id: 106,
          //         title: "التعبئة والتغليف",
          //       },
          //       {
          //         id: 107,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          //   {
          //     title: " أجهزة كبيرة",
          //     id: 108,
          //     children: [
          //       {
          //         id: 109,
          //         title: "مكيفات الهواء  ",
          //       },
          //       {
          //         id: 110,
          //         title: " طباخة ",
          //       },
          //       {
          //         id: 111,
          //         title: " غسالات ومجففات ",
          //       },
          //       {
          //         id: 112,
          //         title: "  المراوح ",
          //       },
          //       {
          //         id: 113,
          //         title: "  اجهزة التجميد ",
          //       },
          //       {
          //         id: 114,
          //         title: "ثلاجات ",
          //       },
          //       {
          //         id: 115,
          //         title: "غير ذالك ",
          //       },
          //     ],
          //   },
          //   {
          //     title: " أجهزة صغيرة",
          //     id: 116,
          //     children: [
          //       {
          //         id: 117,
          //         title: " غلايات",
          //       },
          //       {
          //         id: 118,
          //         title: "خلاط",
          //       },
          //       {
          //         id: 119,
          //         title: "أفران $ التسخين",
          //       },
          //       {
          //         id: 120,
          //         title: "أفران $ التسخين",
          //       },
          //       {
          //         id: 121,
          //         title: "مكنسة كهربائية",
          //       },
          //       {
          //         id: 122,
          //         title: "غير ذالك",
          //       },
          //     ],
          //   },
          // ],
        },
        {
          title: " ألعاب",
          id: 123,
          // children: [
          //   {
          //     id: 124,
          //     title: " بلاي ستيشن",
          //   },
          //   {
          //     id: 125,
          //     title: "اكس بوكس",
          //   },
          //   {
          //     id: 126,
          //     title: " نينتندو",
          //   },

          //   {
          //     id: 127,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " منتجات الأطفال",
          id: 128,
          // children: [
          //   {
          //     id: 129,
          //     title: "لعب الأطفال والرضع",
          //   },
          //   {
          //     id: 130,
          //     title: "ملابس اطفال",
          //   },
          //   {
          //     id: 131,
          //     title: " الحمام ومستلزمات النظافة",
          //   },
          //   {
          //     id: 132,
          //     title: "اللعب والتعليم",
          //   },
          //   {
          //     id: 133,
          //     title: "صحة الأطفال والعناية بالبشرة",
          //   },
          //   {
          //     id: 134,
          //     title: "الحليب والطعام",
          //   },
          //   {
          //     id: 135,
          //     title: " معدات الاطفال",
          //   },

          //   {
          //     id: 136,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: "البقالة",
          id: 137,
          // children: [
          //   {
          //     id: 138,
          //     title: " شاى & قهوة",
          //   },
          //   {
          //     id: 139,
          //     title: "المشروبات",
          //   },
          //   {
          //     id: 140,
          //     title: "منتجات الالبان",
          //   },
          //   {
          //     id: 141,
          //     title: "المخبوزات",
          //   },
          //   {
          //     id: 142,
          //     title: "اللوازم المنزلية",
          //   },
          //   {
          //     id: 143,
          //     title: "الوجبات السريعة",
          //   },
          //   {
          //     id: 144,
          //     title: "المواد الغذائية الأساسية",
          //   },
          //   {
          //     id: 145,
          //     title: "الأغذية المعلبة",
          //   },

          //   {
          //     id: 146,
          //     title: "البهارات & الأعشاب",
          //   },
          //   {
          //     id: 147,
          //     title: " لوازم الخبز والحلويات",
          //   },
          //   {
          //     id: 148,
          //     title: "الحبوب",
          //   },
          //   {
          //     id: 149,
          //     title: "شكلاته & حلويات ",
          //   },
          //   {
          //     id: 150,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " القرطاسية ",
          id: 150,
          // children: [
          //   {
          //     id: 151,
          //     title: " الكتب & المجلات & الدفاتر",
          //   },
          //   {
          //     id: 152,
          //     title: "الرسم وملحقاتها",
          //   },
          //   {
          //     id: 153,
          //     title: "مستلزمات مدرسية",
          //   },
          //   {
          //     id: 154,
          //     title: "مستلزمات مكتبيه",
          //   },
          //   {
          //     id: 155,
          //     title: "مستلزمات هندسية",
          //   },
          //   {
          //     id: 156,
          //     title: "مستلزمات طبية",
          //   },
          //   {
          //     id: 157,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " البناء والكهرباء",
          id: 158,
          // children: [
          //   {
          //     id: 159,
          //     title: " الكهرباء وملحقاتها ",
          //   },
          //   {
          //     id: 160,
          //     title: " البناء وملحقاتها ",
          //   },
          //   {
          //     id: 161,
          //     title: " السباكة وملحقاتها ",
          //   },
          //   {
          //     id: 162,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " المركبات",
          id: 163,
          // children: [
          //   {
          //     id: 164,
          //     title: " السيارات",
          //   },
          //   {
          //     id: 165,
          //     title: " ملحقات السيار",
          //   },

          //   {
          //     id: 166,
          //     title: "الشاحنات والمعدات الثقيلة",
          //   },
          //   {
          //     id: 167,
          //     title: "الدراجات النارية",
          //   },
          //   {
          //     id: 168,
          //     title: "الدراجات الهوائية",
          //   },
          //   {
          //     id: 169,
          //     title: " ملحقات الدراجات",
          //   },
          //   {
          //     id: 170,
          //     title: "غير ذالك",
          //   },
          // ],
        },
        {
          title: " عقارات",
          id: 171,
        },
      ],
    };
  },
  methods: {
    uploadImage(e) {
      const image = e.target.files[0];
      const reader = new FileReader();
      reader.readAsDataURL(image);
      reader.onload = (e) => {
        this.previewImage = e.target.result;
        console.log(this.previewImage);
      };
    },
    previewImage: function (event) {
      var input = event.target;
      if (input.files && input.files[0]) {
        var reader = new FileReader();
        reader.onload = (e) => {
          this.imageData = e.target.result;
        };
        reader.readAsDataURL(input.files[0]);
      }
    },
  },
  computed: {
    currentTitle() {
      switch (this.step) {
        case 1:
          return "Sign-up";
        case 2:
          return "Create a password";
        default:
          return "Account created";
      }
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ShowRoomAddNewCar {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  width: 100%;

  .add-text {
    font-family: $fontfamliy3 !important;
    font-size: 20px;
    color: $fontcolor;
    letter-spacing: 0;
    @media (max-width: 700px) {
      font-size: 17px;
      span {
        font-size: 25px;
      }
    }
    span {
      font-size: 30px;
    }
  }
  ::v-deep .theme--light.v-list-item--active:before {
    opacity: 0;
  }
  .image-preview {
    height: 100px;
    margin: 0 auto;
    // box-shadow: 0 0 0 1px rgb(207, 207, 207);
    // border: 1.5px #fc624d;
    // box-shadow: 0 0 0 1px #fc624d;
    position: relative;
    // border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    .v-icon {
      font-size: 23px;
      color: #fc624d;
    }
    .v-btn {
      position: absolute;
      top: 0;
      right: 0;
      background-color: white;
      color: $color-2 !important;
    }
    div {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
    }
  }
  .photo-text {
    font-size: 14px;
    color: $fontcolor;
    letter-spacing: 0;
    font-weight: 600;
    font-family: sans-serif !important;
    display: block !important;
    text-align: center;
    padding: 5px 5px;
  }
  .preview {
    width: 100%;
    height: 100%;
    // box-shadow: 0 0 0 2px rgb(255, 255, 255);
    display: flex;
    justify-content: center;
    align-items: center;
    // border-radius: 5px;
    // background-color: rgb(255, 255, 255);
    img {
      max-width: 80%;
      max-height: 100%;
    }
  }
  .save-pu-btn {
    font-size: 16px;
    color: white;
    letter-spacing: 0;
    font-weight: 500;
    font-family: $fontfamliy3 !important;
    background-color: $color-2 !important;
  }
}
.cancel-btn {
  font-size: 16px !important;
  color: $fontcolorlinks;
  letter-spacing: 0;
  font-weight: 500;
  font-family: $fontfamliy3 !important;
}
.cover-image-input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  cursor: pointer;
}
.custom-file-input {
  display: none;
}
::v-deep .theme--light.v-input input::placeholder {
  color: rgb(122, 122, 122);
  font-size: 14px !important;
}
::v-deep .v-text-field__suffix {
  font-size: 14px !important;
}

.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
.text-cunt {
  font-size: 17px !important;
  color: $fontcolorlinks;
  letter-spacing: 0.5px;
  font-weight: 600 !important;
  font-family: sans-serif !important;
}
.text {
  letter-spacing: 0px;
  font-weight: 500 !important;
  font-family: $fontfamliy3 !important;
}
//
::v-deep .v-text-field.v-text-field--solo.v-input--dense > .v-input__control {
  min-height: 30px !important;
}
// ::v-deep .v-text-field.v-text-field--solo .v-input__control input {
//   text-align: center;
// }
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
// variation  imag
.image-pre-variation {
  height: 100px;
  margin: 0 auto;
  // box-shadow: 0 0 0 1px rgb(207, 207, 207);
  // border: 1.5px #fc624d;
  background-color: #fc624d;
  position: relative;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .v-icon {
    font-size: 23px;
    color: #ffffff;
  }
  .v-btn {
    position: absolute;
    top: 0;
    right: 0;
    background-color: white;
    color: $color-2 !important;
  }
  div {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  span {
    font-size: 14px;
    color: #fff;
    letter-spacing: 0;
    font-weight: 600;
    font-family: $fontfamliy3 !important;
    margin-top: 5px;
    display: block;
    text-align: center;
  }
}
.pre-variation {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  img {
    max-width: 80%;
    max-height: 100%;
  }
}
</style>
