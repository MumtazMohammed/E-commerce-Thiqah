<template>
  <div class="UserProfileEdit">
    <v-container>
      <v-col class="pt-0" cols="12">
        <v-card-title class="title pt-0"> تعديل الملف الشخصي </v-card-title>
      </v-col>
      <v-row class="justify-space-around">
        <v-col class="my-auto" cols="12" sm="10" md="3">
          <v-card-actions class="pa-0 justify-center">
            <v-avatar size="100" color="white">
              <v-img contain src="@/assets/pp.jpg" alt="@/assets/pp.jpg">
              </v-img>
            </v-avatar>
          </v-card-actions>
          <v-file-input
            label="تغير الصورة الشخصية"
            hide-details
            solo
            prepend-inner-icon="mdi-camera"
            class="input mt-3 elevation-0"
          ></v-file-input>
        </v-col>
        <v-divider vertical class="hidden-sm-and-down"></v-divider>
        <v-col class="" cols="12" sm="10" md="7">
          <span>الأسم كامل :</span>
          <v-text-field
            v-model="UserName"
            label="الأسم كامل"
            solo
            class="input"
          ></v-text-field>
          <span>رقم الهاتف :</span>
          <v-text-field
            v-model="UserPhoneNum"
            label=" هاتف"
            solo
            class="input"
          ></v-text-field>
          <span>البريد الأكتروني :</span>
          <v-text-field
            v-model="Email"
            label=" البريد الأكتروني"
            solo
            class="input"
          ></v-text-field>
          <span>المنطقة :</span>
          <v-text-field
            v-model="UserPlace"
            label=" المنطقة "
            solo
            class="input"
          ></v-text-field>
          <span>الجنس :</span>
          <v-radio-group class="ma-1" row v-model="radioGroup">
            <v-radio label="ذكر" value="ذكر"></v-radio>
            <v-radio label="أنثى" value="أنثى"></v-radio>
          </v-radio-group>
          <v-text-field
            v-model="password"
            :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.min]"
            :type="show1 ? 'text' : 'password'"
            name="input-10-1"
            label="أدخل كلمة المرور الحالي"
            hint="At least 8 characters"
            counter
            class="input"
            @click:append="show1 = !show1"
          ></v-text-field>
          <v-text-field
            v-model="password"
            :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.min]"
            :type="show1 ? 'text' : 'password'"
            name="input-10-1"
            label="أدخل كلمة المرور الجديد"
            hint="At least 8 characters"
            counter
            class="input"
            @click:append="show1 = !show1"
          ></v-text-field>
        </v-col>
        <!-- btn Update Or cancel  -->
        <v-col class="mx-auto" cols="12">
          <v-card-actions class="justify-center">
            <v-btn elevation="0" class="edit-btn" @click="save">
              حفظ التعديل
            </v-btn>
            <v-snackbar
              color="success "
              v-model="hasSaved"
              :timeout="2000"
              absolute
              centered
            >
              <p class="update ma-0">
                <v-icon right>mdi-check-circle-outline </v-icon>
                تم الحفظ
              </p>
            </v-snackbar>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "UserProfileEdit",
  data() {
    return {
      hasSaved: false,
      UserName: "محمد أمين شمسان",
      Email: "momu130399@gmail.com",
      UserIdNum: 15481,
      UserPhoneNum: "01121331731",
      UserPlace: "تعز",
      password: "Password",
      radioGroup: null,
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `The email and password you entered don't match`,
      },
    };
  },
  methods: {
    save() {
      this.hasSaved = true;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.UserProfileEdit {
  width: 100%;
  ::v-deep .v-text-field.v-text-field--solo .v-input__prepend-outer {
    display: none;
  }
  .title {
    color: $fontcolorlinks !important;
    font-size: 18px !important;
    font-family: $fontfamliy2 !important;
    letter-spacing: 0 !important;
  }
  .update {
    color: $fontcolorsm !important;
    font-size: 20px !important;
    font-family: $fontfamliy !important;
    letter-spacing: 0 !important;
  }
  p {
    color: $fontcolorlinks !important;
    font-family: $fontfamliy !important;
    letter-spacing: 0px !important;
    font-size: 18px !important;
  }
  span {
    color: $fontcolorlinks !important;
    font-family: $fontfamliy3 !important;
    letter-spacing: 0px !important;
    font-size: 16px !important;
  }
  .email {
    color: $fontcolorlinks !important;
    font-family: $fontfamliy !important;
    letter-spacing: 1px !important;
    font-size: 18px !important;
  }

  .edit-btn {
    color: $fontcolorsm !important;
    font-size: 16px !important;
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    width: 15% !important;
    background-color: $color-2 !important;
    @media (max-width: 550px) {
      width: 70% !important;
    }
    @media (max-width: 370px) {
      width: 100% !important;
    }
  }
  .input {
    font-size: 18px !important;
    font-family: $fontfamliy !important;
    letter-spacing: 0 !important;
  }
}
</style>
