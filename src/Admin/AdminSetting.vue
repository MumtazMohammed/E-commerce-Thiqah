<template>
  <div class="admin-setting">
    <v-container>
      <v-row class="justify-center">
        <v-col cols="12">
          <v-card-actions class="justify-center">
            <v-avatar size="70" tile color="transparent">
              <v-img
                contain
                src="../assets/outsrc/Tip1.png"
                lazy-src="../assets/outsrc/Tip1.png"
                alt="../assets/outsrc/Tip1.png"
              >
              </v-img>
            </v-avatar>
          </v-card-actions>
          <v-card-actions class="justify-center">
            <v-btn elevation="0" dark class="blue change-logo">
              تغير شعار الموقع
            </v-btn>
          </v-card-actions>
        </v-col>
        <v-col cols="12" sm="8" md="6">
          <v-simple-table>
            <template v-slot:default>
              <tbody>
                <tr v-for="item in desserts" :key="item.name">
                  <td class="table-data">{{ item.name }}</td>
                  <td class="text-center table-data">{{ item.data }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-col>
        <v-col v-if="IsChangeInfo" cols="12" class="py-0">
          <v-card flat color="transparent" max-width="500" class="mx-auto">
            <v-text-field
              class="label-left"
              label="Email address"
              prefix="gmail.com@"
              solo
            ></v-text-field>
            <v-text-field label=" رقم الأتصال" solo></v-text-field>
            <v-text-field label=" رقم الوتس آب" solo></v-text-field>
          </v-card>
        </v-col>
        <v-col cols="12">
          <v-card-actions class="justify-center">
            <v-btn
              v-if="IsChangeInfo"
              @click.prevent="IsChangeInfo = !IsChangeInfo"
              dark
              class="success change-logo"
            >
              حفظ التعديل
            </v-btn>
            <v-btn
              @click.prevent="IsChangeInfo = !IsChangeInfo"
              dark
              class="red change-logo"
              v-text="IsChangeInfo ? CancleChangeInfoText : ChangeInfoText"
            >
            </v-btn>
          </v-card-actions>
        </v-col>
        <!-- password  -->
        <v-col cols="12">
          <v-card-title class="justify-center"> كلمة السر </v-card-title>
          <v-card tile color="transparent" flat max-width="500" class="mx-auto">
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="Normal with hint text"
              hint="At least 8 characters"
              counter
              @click:append="show1 = !show1"
              disabled
              v-if="ChangePassword == false"
            ></v-text-field>
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :rules="[rules.required, rules.emailMatch]"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="كلمة السر السابقة"
              counter
              @click:append="show1 = !show1"
              v-if="ChangePassword"
            ></v-text-field>
            <v-text-field
              v-model="NewPassword"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="كلمة السر الجديدة"
              counter
              @click:append="show1 = !show1"
              v-if="ChangePassword"
            ></v-text-field>
          </v-card>
        </v-col>
        <!-- password change  -->
        <v-card-actions class="justify-center">
          <v-btn
            v-if="ChangePassword"
            @click.prevent="ChangePassword = !ChangePassword"
            dark
            class="success change-logo"
          >
            حفظ التعديل
          </v-btn>
          <v-btn
            @click.prevent="ChangePassword = !ChangePassword"
            dark
            class="red change-logo"
            v-text="ChangePassword ? CancleChangeInfoText : ChangeInfoText"
          >
          </v-btn>
        </v-card-actions>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "AdminSetting",
  data() {
    return {
      IsChangeInfo: false,
      ChangeInfoText: "تعديل  ",
      CancleChangeInfoText: "إلغاء",
      show1: false,
      ChangePassword: false,
      password: "Password",
      NewPassword: null,
      desserts: [
        {
          name: "البريد الأكترواني ",
          data: "mumo17127@gmail.com",
        },
        {
          name: "رقم الأتصال",
          data: 1121331731,
        },
        {
          name: "رقم التس آب",
          data: 1121331731,
        },
      ],
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        emailMatch: () => `كلمة السر غير صحيحة`,
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.admin-setting {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
  padding: $padding;
  font-family: $fontfamliy;
  letter-spacing: 0px;
  .change-logo {
    font-weight: 600 !important;
    letter-spacing: 0 !important;
  }
}
::v-deep .label-left label.v-label.theme--light {
  left: 0 !important;
  transform-origin: top left !important;
  position: absolute !important;
}
::v-deep .label-left.v-text-field.v-text-field--solo .v-input__control input {
  caret-color: auto;
  text-align: left;
}
.table-data {
  font-size: 17px !important;
  font-family: $fontfamliy;
}
</style>
