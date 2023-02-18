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
    <v-container class="">
      <v-card tile flat class="mx-auto" min-height="600">
        <v-window v-model="step" style="min-height: 548px">
          <!-- select the categories and fill the goods name & number -->
          <v-window-item :value="1">
            <v-card flat tile class="pa-2">
              <div>
                <span class="add-text">
                  <span class="red--text ml-1">*</span>
                  اختيار فئة المنتج .
                </span>
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
              </div>
              <div v-if="CategoryOne">
                <span class="add-text">
                  <span class="red--text ml-1">*</span>
                  حدد الفئة المناسبة لمنتجك.
                </span>
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
              </div>
              <v-col v-if="NameAndNumber" cols="12" class="pa-2">
                <span class="add-text">
                  <span class="red--text ml-1">*</span>
                  اسم المنتج & رقم المنتج.
                </span>
                <v-text-field
                  class="ma-0 pa-0"
                  hide-details
                  placeholder="أسم المنتج *"
                  v-model="ProductName"
                ></v-text-field>
                <v-text-field
                  class="ma-0"
                  hide-details
                  placeholder="رقم المنتج *"
                  v-model="ProductNumber"
                ></v-text-field>
              </v-col>
            </v-card>
          </v-window-item>
          <!-- Add the the images  -->
          <v-window-item :value="2">
            <div>
              <span class="add-text pa-3">
                <span class="red--text ml-1">*</span>
                قم بتحميل صورة أمامية واضحة لمنتجك .
              </span>
              <v-row no-gutters class="pa-0">
                <v-col class="pa-2 mx-auto" cols="">
                  <div class="image-preview ma-1">
                    <div v-if="imageData.length <= 0">
                      <v-icon> mdi-plus </v-icon>
                      <span>صورة الغلاف</span>
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
                </v-col>
              </v-row>
            </div>
            <div>
              <span class="add-text pa-3">
                <span class="red--text ml-1">*</span>
                قم بتحميل 3 صور للمنتج على الاقل .
              </span>
              <v-row no-gutters class="pa-0">
                <v-col class="pa-2" cols="4" v-for="(imag, i) in 3" :key="i">
                  <div class="image-preview ma-1">
                    <div v-if="imageData.length <= 0">
                      <v-icon> mdi-plus </v-icon>
                      <span>صورة الغلاف</span>
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
                </v-col>
              </v-row>
            </div>
            <div>
              <span class="add-text pa-3">
                <span class="red--text ml-1">*</span>
                ماهية ألوان منتجك .
              </span>
              <v-row no-gutters class="pa-0">
                <v-col class="pa-2" cols="4" v-for="(imag, i) in 3" :key="i">
                  <div class="image-preview ma-1">
                    <div v-if="imageData.length <= 0">
                      <v-icon> mdi-plus </v-icon>
                      <span>صورة المنتج يظهر بها الوان اذا توفر</span>
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
                  <v-text-field
                    class="ma-1"
                    dense
                    outlined
                    flat
                    label="ألون"
                    solo
                    hide-details
                  ></v-text-field>
                </v-col>
              </v-row>
            </div>
          </v-window-item>

          <!--  fill the  Information -->
          <v-window-item :value="3">
            <v-card flat class="pa-2">
              <v-card-actions class="py-4 px-0">
                <v-checkbox
                  hide-details=""
                  class="ma-0 pa-0"
                  color="success"
                  v-model="size"
                ></v-checkbox>
                <span
                  class="pa-0"
                  :class="size == true ? 'success--text' : 'grey--text '"
                >
                  هل يوجد مقاسات للمنتج :
                </span>
              </v-card-actions>
              <v-card
                v-if="size"
                class="mr-2"
                style="overflow: hidden"
                outlined
                max-width="230"
              >
                <v-card-actions class="pa-0">
                  <v-btn
                    class="px-1"
                    tile
                    elevation="0"
                    height="30"
                    min-width="35"
                    @click="Quantity++"
                  >
                    <v-icon size="17">mdi-plus</v-icon>
                  </v-btn>
                  <v-text-field
                    v-model="Quantity"
                    solo
                    dense
                    flat
                    hide-details
                    placeholder="كم عدد المقاسات"
                    type="number"
                  ></v-text-field>
                  <v-btn
                    class="px-1"
                    tile
                    elevation="0"
                    height="30"
                    min-width="35"
                    @click="Quantity--"
                  >
                    <v-icon size="17">mdi-minus</v-icon>
                  </v-btn>
                </v-card-actions>
              </v-card>
              <v-row no-gutters v-if="size">
                <v-col class="pa-2" cols="6" md="3" lg="3" sm="4">
                  <v-text-field
                    placeholder="المقاس ( 1 )"
                    hide-details
                    outlined
                    dense
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-card-actions class="py-4 px-0">
                <v-checkbox
                  hide-details=""
                  class="ma-0 pa-0"
                  color="success"
                  v-model="model"
                ></v-checkbox>
                <v-card-text
                  class="pa-0"
                  :class="model == true ? 'success--text' : 'grey--text '"
                >
                  هل يوجد موديل للمنتج :
                </v-card-text>
              </v-card-actions>
              <div v-if="model">
                <v-card
                  class="mr-2"
                  style="overflow: hidden"
                  outlined
                  max-width="230"
                >
                  <v-card-actions class="pa-0">
                    <v-btn
                      class="px-1"
                      tile
                      elevation="0"
                      height="30"
                      min-width="35"
                      @click="Quantity++"
                    >
                      <v-icon size="17">mdi-plus</v-icon>
                    </v-btn>
                    <v-text-field
                      v-model="Quantity"
                      solo
                      dense
                      flat
                      hide-details
                      placeholder="كم عدد الموديلات"
                      type="number"
                    ></v-text-field>
                    <v-btn
                      class="px-1"
                      tile
                      elevation="0"
                      height="30"
                      min-width="35"
                      @click="Quantity--"
                    >
                      <v-icon size="17">mdi-minus</v-icon>
                    </v-btn>
                  </v-card-actions>
                </v-card>
                <v-row no-gutters>
                  <v-col class="pa-2" cols="6" md="3" lg="3" sm="4">
                    <v-text-field
                      placeholder="موديل ( 1 )"
                      hide-details
                      outlined
                      dense
                    ></v-text-field>
                  </v-col>
                </v-row>
              </div>
              <v-card-actions class="py-4 px-0">
                <v-checkbox
                  hide-details=""
                  color="success"
                  class="ma-0 pa-0"
                  v-model="flavor"
                ></v-checkbox>
                <v-card-text
                  class="pa-0"
                  :class="flavor == true ? 'success--text' : 'grey--text '"
                >
                  هل يوجد نكهات للمنتج :
                </v-card-text>
              </v-card-actions>
              <div v-if="flavor">
                <v-card
                  class="mr-2"
                  style="overflow: hidden"
                  outlined
                  max-width="230"
                >
                  <v-card-actions class="pa-0">
                    <v-btn
                      class="px-1"
                      tile
                      elevation="0"
                      height="30"
                      min-width="35"
                      @click="Quantity++"
                    >
                      <v-icon size="17">mdi-plus</v-icon>
                    </v-btn>
                    <v-text-field
                      v-model="Quantity"
                      solo
                      dense
                      flat
                      hide-details
                      placeholder="كم عدد النكات"
                      type="number"
                    ></v-text-field>
                    <v-btn
                      class="px-1"
                      tile
                      elevation="0"
                      height="30"
                      min-width="35"
                      @click="Quantity--"
                    >
                      <v-icon size="17">mdi-minus</v-icon>
                    </v-btn>
                  </v-card-actions>
                </v-card>
                <v-row no-gutters>
                  <v-col class="pa-2" cols="6" md="3" lg="3" sm="4">
                    <v-text-field
                      placeholder="نكهة ( 1 )"
                      hide-details
                      outlined
                      dense
                    ></v-text-field>
                  </v-col>
                </v-row>
              </div>
            </v-card>
            <v-col cols="12" class="pa-2">
              <v-textarea
                outlined
                flat
                placeholder=" تفاصيل المنتج"
              ></v-textarea>
            </v-col>
            <v-card flat class=" ">
              <div style="flex-basis: 40%">
                <v-card-text class="pa-2"> رقم المنتج: </v-card-text>
                <v-text-field dense hide-details=""></v-text-field>
              </div>
              <div style="flex-basis: 40%">
                <v-card-text class="pa-2"> السعر: </v-card-text>
                <v-text-field
                  type="number"
                  suffix="ريال"
                  dense
                  hide-details=""
                ></v-text-field>
              </div>
              <div style="flex-basis: 40%">
                <v-card-text class="pa-2"> الكمية: </v-card-text>
                <v-text-field
                  type="number"
                  dense
                  hide-details=""
                ></v-text-field>
              </div>
            </v-card>
          </v-window-item>
        </v-window>

        <v-divider></v-divider>

        <v-card-actions>
          <v-btn :disabled="step === 1" text @click="step--"> الرجوع </v-btn>
          <v-spacer></v-spacer>
          <v-btn
            :disabled="step === 3"
            color="primary"
            depressed
            @click="step++"
          >
            التالي
          </v-btn>
        </v-card-actions>
      </v-card>

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
      ProductName: "",
      ProductNumber: "",
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
  min-height: calc(100vh - 128px);

  .add-text {
    font-size: 20px;
    line-height: 1.5;
    color: $fontcolorlinks;
    letter-spacing: 0;
    span {
      font-size: 25px !important;
    }
  }
  .categories-text {
    font-size: 14px;
    height: 20px;
    color: $fontcolorlinks;
    letter-spacing: 0;
    font-family: $fontfamliy3 !important;
  }

  .next-btn {
    font-size: 18px;
    color: $fontcolorlinks;
    letter-spacing: 0;
    font-weight: 500;
    font-family: $fontfamliy3 !important;
  }

  ::v-deep .v-input__slot {
    padding: 0 10px !important;
  }
  ::v-deep .theme--light.v-list-item--active:before {
    opacity: 0;
  }
  .image-preview {
    height: 100px;
    margin: 0 auto;
    // box-shadow: 0 0 0 1px rgb(207, 207, 207);
    // border: 1.5px #fc624d;
    box-shadow: 0 0 0 1px #fc624d;
    position: relative;
    border-radius: 5px;
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
    span {
      font-size: 14px;
      color: $fontcolorlinks;
      letter-spacing: 0;
      font-weight: 600;
      font-family: $fontfamliy3 !important;
      margin-top: 5px;
      display: block;
      text-align: center;
    }
  }
  .preview {
    width: 100%;
    height: 100%;
    box-shadow: 0 0 0 2px rgb(255, 255, 255);
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 5px;
    background-color: rgb(255, 255, 255);
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
  color: black;
}

.titel {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  font-size: 18px !important;
}
.card-wrap {
  min-height: calc(100vh - 180px);
  @media (max-width: 600px) {
    min-height: calc(100vh - 110px);
  }
}
//
::v-deep .v-text-field.v-text-field--solo.v-input--dense > .v-input__control {
  min-height: 30px !important;
}
::v-deep .v-text-field.v-text-field--solo .v-input__control input {
  text-align: center;
}
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
