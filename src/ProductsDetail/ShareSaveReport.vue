<template>
  <div class="share">
    <v-card-actions class="pa-0 justify-start">
      <!-- favourites   -->
      <v-btn @click="isSaved = !isSaved" icon class="btn">
        <v-icon
          v-text="isSaved ? 'mdi-cards-heart' : 'mdi-cards-heart-outline'"
          color="#848484"
          class="icon"
          :class="isSaved ? 'red--text' : ''"
        >
        </v-icon>
      </v-btn>
      <!-- Share to  -->
      <v-dialog class="dialog" transition="slide-y-transition" max-width="300">
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon color="#848484" class="icon"> mdi-share-variant </v-icon>
          </v-btn>
        </template>
        <template v-slot:default="dialog">
          <v-card>
            <v-card-actions class="flex-column">
              <v-btn elevation="2" width="90%" class="btn-share ma-0 my-2" text>
                واتس آب
              </v-btn>
              <v-btn
                elevation="2"
                large
                width="90%"
                class="btn-share ma-0 my-2"
                text
              >
                فيسبوك
              </v-btn>
              <v-btn
                elevation="2"
                large
                width="90%"
                class="btn-copy-link ma-0 my-2"
                text
              >
                نسخ الرابط
              </v-btn>

              <v-btn
                class="v-btn-close"
                color="red"
                elevation="2"
                width="90%"
                large
                @click="dialog.value = false"
              >
                أغلاق
              </v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
      <!-- <v-divider vertical class="mx-2"></v-divider>
      <v-dialog
        class="dialog"
        persistent
        transition="slide-y-transition"
        max-width="500"
        scrollable
        z-index="202"
      >
        <template v-slot:activator="{ on, attrs }">
          <a class="btn" v-bind="attrs" v-on="on">
            <v-icon color="red" right class="icon"> mdi-flag-variant </v-icon>
            إبلاغ
          </a>
        </template>
        <template v-slot:default="dialog">
          <v-card height="100%">
            <v-toolbar elevation="1">
              <v-toolbar-title class="share">
                الإبلاغ عن هذا الإعلان
              </v-toolbar-title>
              <v-spacer></v-spacer>
              <v-btn @click="dialog.value = false" icon>
                <v-icon>mdi-close</v-icon>
              </v-btn>
            </v-toolbar>
            <div class="pa-3">
              <v-row>
                <v-col cols="12" class="pb-0">
                  <v-card-text class="share pa-1">
                    نوع البلاغ
                    <span class="red--text">*</span>
                  </v-card-text>
                  <v-combobox
                    solo
                    dense
                    v-model="select"
                    :items="items"
                  ></v-combobox>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-card-text class="share pa-1">
                    الأسم كامل
                    <span class="red--text">*</span>
                  </v-card-text>
                  <v-text-field
                    class="text-field"
                    ref="name"
                    v-model="name"
                    :rules="[() => !!name || 'هذه الخانة مطلوبه']"
                    :error-messages="errorMessages"
                    solo
                    dense
                    required
                  ></v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-card-text class="share pa-1">
                    رقم الجوال
                    <span class="red--text">*</span>
                  </v-card-text>
                  <v-text-field
                    v-model="Num"
                    :rules="[() => !!Num || 'هذه الخانة مطلوبه']"
                    :error-messages="errorMessages"
                    solo
                    dense
                    required
                  ></v-text-field>
                </v-col>
                <v-col cols="12" class="py-0">
                  <v-card-text class="share pa-1">
                    أترك تعليقاَ
                    <span class="red--text">*</span>
                  </v-card-text>
                  <v-textarea
                    :rules="[() => !!Message || 'هذه الخانة مطلوبه']"
                    solo
                    no-resize
                    rows="6"
                    name="input-7-4"
                  ></v-textarea>
                </v-col>
                <v-col cols="12" class="pt-0">
                  <v-btn
                    elevation="0"
                    outlined
                    block
                    color="red"
                    class="report-btn"
                  >
                    إرسال البلاغ
                  </v-btn>
                </v-col>
              </v-row>
            </div>
          </v-card>
        </template>
      </v-dialog> -->
      <!--  -->
    </v-card-actions>
  </div>
</template>
<script>
// import CarData from "../data-json/All-Car.json";
export default {
  name: "ShareSaveReport",
  data() {
    return {
      isSaved: false,
      report: false,
      isSavedIcon: "mdi-heart",
      isNotSavedIcon: " mdi-heart-outline",
      errorMessages: "",
      name: null,
      Num: null,
      Message: null,
      select: ["مباع"],
      items: [
        "مباع",
        "تكرار الإعلان",
        "صنع وطراز غير صحيح / غير متسق المعلن عنه",
        "ناقل الحركة غير صحيح / غير متسق / عدد الكيلومترات / الموقع",
        "التسعير غير الصحيح / غير المتسق",
        "عام غير صحيح",
        "غير صحيح / طمس / لا توجد صور",
        "رقم الاتصال غير صحيح",
        "عرض خدمات أخرى غير ذات صلة",
      ],
    };
  },

  watch: {
    name() {
      this.errorMessages = "";
    },
  },

  methods: {
    addressCheck() {
      this.errorMessages =
        this.address && !this.name ? `Hey! I'm required` : "";

      return true;
    },
    resetForm() {
      this.errorMessages = [];
      this.formHasErrors = false;

      Object.keys(this.form).forEach((f) => {
        this.$refs[f].reset();
      });
    },
    submit() {
      this.formHasErrors = false;

      Object.keys(this.form).forEach((f) => {
        if (!this.form[f]) this.formHasErrors = true;

        this.$refs[f].validate(true);
      });
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.share {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0;
}
.report-btn {
  font-size: 17px !important;
  letter-spacing: 0 !important;
  color: $fontcolorsm !important;
  font-family: $fontfamliy3 !important;
  font-weight: 500;
}
.v-dialog__content.v-dialog__content--active::v-deep .v-dialog--active {
  margin: 5px !important;
}

.v-btn-close {
  font-size: 18px !important;
  letter-spacing: 0;
  color: $fontcolorsm !important;
  font-family: $fontfamliy3 !important;
}
.btn-share {
  color: $fontcolor;
  letter-spacing: 0;
  font-family: $fontfamliy3;
  font-size: 17px !important;
  transition: transform 0.3s ease;
}

.btn-copy-link {
  color: $fontcolor !important;
  letter-spacing: 0;
  font-family: $fontfamliy;
  font-size: 18px !important;
  transition: transform 0.3s ease;
}
.icon {
  @media (max-width: 600px) {
    font-size: 18px !important;
  }
}
a {
  text-align: center !important;
}
::v-deep .v-dialog:not(.v-dialog--fullscreen) {
  max-height: 100%;
}
::v-deep
  .v-autocomplete:not(.v-input--is-disabled).v-select.v-text-field
  input {
  font-family: $fontfamliy !important;
  letter-spacing: 0 !important;
  font-weight: 500;
  height: 50px;
}
::v-deep .v-list-item__content {
  font-family: $fontfamliy !important;
  letter-spacing: 0 !important;
  font-weight: 500;
  // height: 70px;
}
::v-deep .v-list-item__title {
  height: 20px;
}
::v-deep .v-overlay.v-overlay--active.theme--dark {
  z-index: 202 !important;
}
</style>
