<template>
  <div class="ShowRoomAddNewCar">
    <v-container>
      <v-sheet flat color="transparent" min-height="400">
        <v-card-actions class="justify-center">
          <v-btn
            mn-width="170"
            depressed
            elevation="0"
            class="cancel-btn rounded-0 rounded-r-lg"
          >
            حذف المنتج
          </v-btn>
          <v-btn mn-width="170" elevation="0" class="cancel-btn ma-0 rounded-0">
            توقيف المنتج
          </v-btn>
          <v-btn
            mn-width="170"
            elevation="0"
            class="cancel-btn ma-0 rounded-0 rounded-l-lg"
          >
            نفذت الكمية
          </v-btn>
        </v-card-actions>
        <v-card flat class="pa-3">
          <v-card-actions class="justify-center">
            <div class="image-preview mx-1" v-for="(imag, i) in 7" :key="i">
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
          </v-card-actions>
        </v-card>
        <v-card flat class="pa-3 mt-2">
          <v-col cols="12" class="pb-0">
            <v-text-field placeholder="أسم المنتج "></v-text-field>
          </v-col>
          <v-col cols="12" class="pt-0">
            <v-col cols="12" class="py-0">
              <v-card-actions class="py-4 px-0">
                <v-checkbox
                  hide-details=""
                  color="success"
                  class="ma-0 pa-0"
                  v-model="color"
                ></v-checkbox>
                <v-card-text
                  class="pa-0"
                  :class="color == true ? 'success--text' : 'grey--text '"
                >
                  هل يوجد ألوان للمنتج :
                </v-card-text>
              </v-card-actions>
              <v-select
                :disabled="!color"
                :items="items"
                chips
                multiple
                outlined
                dense
                clearable
                color="success"
                hide-details
              ></v-select>
            </v-col>
            <v-col cols="12" class="py-0">
              <v-card-actions class="py-4 px-0">
                <v-checkbox
                  hide-details=""
                  class="ma-0 pa-0"
                  color="success"
                  v-model="size"
                ></v-checkbox>
                <v-card-text
                  class="pa-0"
                  :class="size == true ? 'success--text' : 'grey--text '"
                >
                  هل يوجد مقاسات للمنتج :
                </v-card-text>
              </v-card-actions>
              <v-select
                :disabled="!size"
                :items="items"
                chips
                multiple
                outlined
                dense
                clearable
                color="success"
                hide-details
              ></v-select>
            </v-col>
            <v-col cols="12" class="py-0">
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
              <v-select
                :disabled="!model"
                :items="items"
                chips
                multiple
                outlined
                dense
                clearable
                color="success"
                hide-details
              ></v-select>
            </v-col>
            <v-col cols="12" class="py-0">
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
              <v-select
                :disabled="!flavor"
                :items="items"
                chips
                multiple
                outlined
                dense
                clearable
                color="success"
                hide-details
              ></v-select>
            </v-col>
          </v-col>
        </v-card>
        <v-card flat class="pa-3 mt-2">
          <v-col cols="12" class="py-0">
            <v-textarea
              solo
              color="#fc624d"
              name="input-7-4"
              placeholder=" تفاصيل المنتج"
            ></v-textarea>
          </v-col>
        </v-card>
        <v-card flat class="pa-3 pb-6 mt-2">
          <div>
            <v-card-text class="pa-2"> رقم المنتج: </v-card-text>
            <v-text-field dense hide-details=""></v-text-field>
          </div>
          <div>
            <v-card-text class="pa-2"> السعر: </v-card-text>
            <v-text-field
              type="number"
              suffix="ريال"
              dense
              hide-details=""
              class="price"
            ></v-text-field>
          </div>
          <div>
            <v-card-text class="pa-2"> الكمية: </v-card-text>
            <v-text-field type="number" dense hide-details=""></v-text-field>
          </div>
        </v-card>
        <v-card-actions class="justify-center pa-4">
          <v-btn
            width="200"
            depressed
            elevation="0"
            class="save-pu-btn rounded-0"
          >
            احفظ
          </v-btn>
          <v-btn width="200" elevation="0" class="cancel-btn ma-0 rounded-0">
            إلغاء
          </v-btn>
        </v-card-actions>
      </v-sheet>
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
      color: false,
      size: false,
      model: false,
      flavor: false,
      //
      items: ["foo", "bar", "fizz", "buzz"],
      value: ["foo", "bar", "fizz", "buzz"],
      step: 1,
      imageData: "",
      Categories: [
        {
          title: "الجوالات  والأجهزة اللوحية",
          id: 1,
          children: [
            {
              id: 2,
              title: "جوالات",
            },
            {
              id: 3,
              title: "أجهزة لوحية",
            },
            {
              id: 4,
              title: "أغطية حماية",
            },
            {
              id: 5,
              title: "حماية الشاشة",
            },
            {
              id: 6,
              title: "شواحن محمولة & وبطاريات",
            },
            {
              id: 7,
              title: "الكابلات والشواحن",
            },
            {
              id: 8,
              title: "سماعات",
            },
            {
              id: 9,
              title: "الساعات الذكية",
            },
            {
              id: 10,
              title: " اكسسوارات",
            },
            {
              id: 11,
              title: " غير ذالك",
            },
          ],
        },
        {
          title: " الحواسيب",
          id: 12,
          children: [
            {
              id: 13,
              title: "أجهزة الكمبيوتر المكتبية",
            },
            {
              id: 14,
              title: " أجهزة الكمبيوتر المحمولة",
            },
            {
              id: 15,
              title: " ملحقات الكمبيوتر ",
            },
            {
              id: 16,
              title: " ملحقات الكمبيوتر المحمولة",
            },
            {
              id: 17,
              title: " الطابعات وأجهزة العرض",
            },
            {
              id: 18,
              title: "الأنترنت والشبكات",
            },
            {
              id: 19,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " الأزياء",
          id: 20,
          children: [
            {
              title: " رجالي",
              id: 21,
              children: [
                {
                  id: 22,
                  title: "الملابس الداخلية",
                },
                {
                  id: 23,
                  title: " ملابس خارجية",
                },

                {
                  id: 24,
                  title: "حقائب  ",
                },
                {
                  id: 25,
                  title: "أحذية",
                },
                {
                  id: 26,
                  title: " بناطيل",
                },
                {
                  id: 27,
                  title: " أطقم",
                },
                {
                  id: 28,
                  title: "قمصان",
                },
                {
                  id: 29,
                  title: " ملابس النوم والبجامات",
                },
                {
                  id: 30,
                  title: "الجوارب",
                },
                {
                  id: 31,
                  title: " بدلات",
                },
                {
                  id: 32,
                  title: " فنايل",
                },
                {
                  id: 33,
                  title: "بلايز",
                },
                {
                  id: 34,
                  title: "ملابس ",
                },
                {
                  id: 35,
                  title: "ساعات  ",
                },
                {
                  id: 36,
                  title: "نظارات  ",
                },
                {
                  id: 37,
                  title: "أكسسورات  ",
                },
                {
                  id: 38,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: " نسائي",
              id: 39,
              children: [
                {
                  id: 40,
                  title: "الملابس الداخلية",
                },
                {
                  id: 41,
                  title: " ملابس خارجية",
                },

                {
                  id: 42,
                  title: "حقائب  ",
                },
                {
                  id: 43,
                  title: "أحذية",
                },
                {
                  id: 44,
                  title: " بناطيل",
                },
                {
                  id: 45,
                  title: " أطقم",
                },
                {
                  id: 46,
                  title: "قمصان",
                },
                {
                  id: 47,
                  title: " ملابس النوم والبجامات",
                },
                {
                  id: 48,
                  title: "الجوارب",
                },
                {
                  id: 49,
                  title: " بدلات",
                },
                {
                  id: 50,
                  title: " فنايل",
                },
                {
                  id: 51,
                  title: "بلايز",
                },
                {
                  id: 52,
                  title: "ملابس ",
                },
                {
                  id: 53,
                  title: "ساعات  ",
                },
                {
                  id: 54,
                  title: "نظارات  ",
                },
                {
                  id: 55,
                  title: "أكسسورات  ",
                },
                {
                  id: 56,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: " أطفالي",
              id: 57,
              children: [
                {
                  id: 58,
                  title: "ملابس ولأدي ",
                },
                {
                  id: 59,
                  title: "ملابس بناتي ",
                },
                {
                  id: 60,
                  title: "حقائب أطفالي ",
                },
                {
                  id: 61,
                  title: "أحذية بناتي",
                },
                {
                  id: 62,
                  title: "أحذية ولأدي",
                },
                {
                  id: 63,
                  title: "غير ذالك ",
                },
              ],
            },
          ],
        },
        {
          title: "الصحة & الجمال",
          id: 64,
          children: [
            {
              title: " مساحيق التجميل",
              id: 65,
              children: [
                {
                  id: 66,
                  title: " مكياج خافي عيوب ومصحح لون البشرة",
                },
                {
                  id: 67,
                  title: "كريم أساس",
                },
                {
                  id: 68,
                  title: "ملمع شفاه",
                },
                {
                  id: 69,
                  title: "محدد شفاة",
                },
                {
                  id: 70,
                  title: " أحمر شفاه",
                },
                {
                  id: 71,
                  title: " كحل",
                },
                {
                  id: 72,
                  title: "ماسكارا",
                },
                {
                  id: 73,
                  title: "ايشادو",
                },
                {
                  id: 74,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: "العناية بالشعر",
              id: 75,
              children: [
                {
                  id: 76,
                  title: " العناية بالشعر وفروة الرأس",
                },
                {
                  id: 77,
                  title: "إكسسوارات الشعر",
                },
                {
                  id: 78,
                  title: "شامبو & بلسم",
                },
                {
                  id: 79,
                  title: "مجفف الشعر & وغيرها",
                },
                {
                  id: 80,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: "العناية بالجسم ",
              id: 81,
              children: [
                {
                  id: 82,
                  title: "الفتمينات & مكملات غذائيه",
                },
                {
                  id: 83,
                  title: "المناشف   ",
                },
                {
                  id: 84,
                  title: "مكينة حلاقة رجاليه  ",
                },
                {
                  id: 85,
                  title: "مكينة حلاقة نسائيه  ",
                },
                {
                  id: 86,
                  title: "صابون الجسم & كريم الترطيب &العناية",
                },
                {
                  id: 87,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: "العطور",
              id: 88,
              children: [
                {
                  id: 89,
                  title: "عطور رجالي  ",
                },
                {
                  id: 90,
                  title: "عطور نسائي ",
                },
                {
                  id: 91,
                  title: "غير ذالك",
                },
              ],
            },
          ],
        },
        {
          title: " اثاث منزلية & مكتبية ",
          id: 92,
          children: [
            {
              title: "المنزل والمطبخ",
              id: 93,
              children: [
                {
                  id: 94,
                  title: "الحمامات",
                },
                {
                  id: 95,
                  title: "الفراش",
                },
                {
                  id: 96,
                  title: "ديكور المنزل",
                },
                {
                  id: 97,
                  title: " الأثاث المنزلي",
                },
                {
                  id: 98,
                  title: " المكانس والعناية بالأرضيات",
                },
                {
                  id: 99,
                  title: " تجهيزات المطابخ",
                },
                {
                  id: 100,
                  title: "الخبز",
                },
                {
                  id: 101,
                  title: "السكاكين وأدوات المطبخ",
                },
                {
                  id: 102,
                  title: "  غير ذالك",
                },
              ],
            },
            {
              title: " المنتجات المكتبية",
              id: 103,
              children: [
                {
                  id: 104,
                  title: "اللوازم المكتبية والمدرسية",
                },
                {
                  id: 105,
                  title: " أثاث مكتبي وإنارة",
                },
                {
                  id: 106,
                  title: "التعبئة والتغليف",
                },
                {
                  id: 107,
                  title: "غير ذالك",
                },
              ],
            },
            {
              title: " أجهزة كبيرة",
              id: 108,
              children: [
                {
                  id: 109,
                  title: "مكيفات الهواء  ",
                },
                {
                  id: 110,
                  title: " طباخة ",
                },
                {
                  id: 111,
                  title: " غسالات ومجففات ",
                },
                {
                  id: 112,
                  title: "  المراوح ",
                },
                {
                  id: 113,
                  title: "  اجهزة التجميد ",
                },
                {
                  id: 114,
                  title: "ثلاجات ",
                },
                {
                  id: 115,
                  title: "غير ذالك ",
                },
              ],
            },
            {
              title: " أجهزة صغيرة",
              id: 116,
              children: [
                {
                  id: 117,
                  title: " غلايات",
                },
                {
                  id: 118,
                  title: "خلاط",
                },
                {
                  id: 119,
                  title: "أفران $ التسخين",
                },
                {
                  id: 120,
                  title: "أفران $ التسخين",
                },
                {
                  id: 121,
                  title: "مكنسة كهربائية",
                },
                {
                  id: 122,
                  title: "غير ذالك",
                },
              ],
            },
          ],
        },
        {
          title: " ألعاب",
          id: 123,
          children: [
            {
              id: 124,
              title: " بلاي ستيشن",
            },
            {
              id: 125,
              title: "اكس بوكس",
            },
            {
              id: 126,
              title: " نينتندو",
            },

            {
              id: 127,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " منتجات الأطفال",
          id: 128,
          children: [
            {
              id: 129,
              title: "لعب الأطفال والرضع",
            },
            {
              id: 130,
              title: "ملابس اطفال",
            },
            {
              id: 131,
              title: " الحمام ومستلزمات النظافة",
            },
            {
              id: 132,
              title: "اللعب والتعليم",
            },
            {
              id: 133,
              title: "صحة الأطفال والعناية بالبشرة",
            },
            {
              id: 134,
              title: "الحليب والطعام",
            },
            {
              id: 135,
              title: " معدات الاطفال",
            },

            {
              id: 136,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: "البقالة",
          id: 137,
          children: [
            {
              id: 138,
              title: " شاى & قهوة",
            },
            {
              id: 139,
              title: "المشروبات",
            },
            {
              id: 140,
              title: "منتجات الالبان",
            },
            {
              id: 141,
              title: "المخبوزات",
            },
            {
              id: 142,
              title: "اللوازم المنزلية",
            },
            {
              id: 143,
              title: "الوجبات السريعة",
            },
            {
              id: 144,
              title: "المواد الغذائية الأساسية",
            },
            {
              id: 145,
              title: "الأغذية المعلبة",
            },

            {
              id: 146,
              title: "البهارات & الأعشاب",
            },
            {
              id: 147,
              title: " لوازم الخبز والحلويات",
            },
            {
              id: 148,
              title: "الحبوب",
            },
            {
              id: 149,
              title: "شكلاته & حلويات ",
            },
            {
              id: 150,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " القرطاسية ",
          id: 150,
          children: [
            {
              id: 151,
              title: " الكتب & المجلات & الدفاتر",
            },
            {
              id: 152,
              title: "الرسم وملحقاتها",
            },
            {
              id: 153,
              title: "مستلزمات مدرسية",
            },
            {
              id: 154,
              title: "مستلزمات مكتبيه",
            },
            {
              id: 155,
              title: "مستلزمات هندسية",
            },
            {
              id: 156,
              title: "مستلزمات طبية",
            },
            {
              id: 157,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " البناء والكهرباء",
          id: 158,
          children: [
            {
              id: 159,
              title: " الكهرباء وملحقاتها ",
            },
            {
              id: 160,
              title: " البناء وملحقاتها ",
            },
            {
              id: 161,
              title: " السباكة وملحقاتها ",
            },
            {
              id: 162,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " المركبات",
          id: 163,
          children: [
            {
              id: 164,
              title: " السيارات",
            },
            {
              id: 165,
              title: " ملحقات السيار",
            },

            {
              id: 166,
              title: "الشاحنات والمعدات الثقيلة",
            },
            {
              id: 167,
              title: "الدراجات النارية",
            },
            {
              id: 168,
              title: "الدراجات الهوائية",
            },
            {
              id: 169,
              title: " ملحقات الدراجات",
            },
            {
              id: 170,
              title: "غير ذالك",
            },
          ],
        },
        {
          title: " عقارات",
          id: 171,
          children: [
            {
              id: 172,
              title: "الأراضي",
            },
            {
              id: 173,
              title: " العماير",
            },
            {
              id: 174,
              title: " الفلل",
            },
            {
              id: 175,
              title: "غير ذالك",
            },
          ],
        },
      ],
    };
  },
  computed: {
    currentTitle() {
      switch (this.step) {
        case 1:
          return "الرجاء اختيار الفئة المناسبة لمنتجك.";
        default:
          return "إضافة معلومات المنتج";
      }
    },
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
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ShowRoomAddNewCar {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
  width: 100%;
  min-height: calc(100vh - 100px);
  .add-text {
    font-size: 23px;
    line-height: 1.5;
    color: $fontcolorlinks;
    letter-spacing: 0;
    span {
      font-size: 15px;
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
    width: 100px;
    height: 100px;

    // box-shadow: 0 0 0 1px rgb(207, 207, 207);
    border: 1.5px dashed #1e88e5;
    position: relative;
    border-radius: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    .v-icon {
      font-size: 23px;
      color: #1e88e5;
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
      font-family: $fontfamliy2 !important;
      margin-top: 5px;
      display: block;
      text-align: center;
    }
  }
  .preview {
    width: 100%;
    height: 100%;
    box-shadow: 0 0 0 3px rgb(255, 255, 255);
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
::v-deep .v-input__slot {
  padding: 0;
}
::v-deep
  .theme--light.v-text-field--outlined:not(.v-input--is-focused):not(.v-input--has-state)
  > .v-input__control
  > .v-input__slot
  fieldset {
  color: #4caf50;
}
::v-deep
  .theme--light.v-text-field--outlined:not(.v-input--is-focused).v-input--is-disabled
  > .v-input__control
  > .v-input__slot
  fieldset {
  color: #7d7d7d6e;
}
::v-deep .price .v-input__slot {
  padding-left: 0px !important;
}
</style>
