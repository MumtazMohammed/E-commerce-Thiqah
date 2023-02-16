<template>
  <div class="ShowRoomInfoSetting">
    <v-container>
      <v-row class="justify-center">
        <v-col cols="12" sm="6" md="5" class="my-auto pa-0 pa-md-3 pa-lg-3">
          <v-card-actions class="justify-center">
            <div class="image-preview mx-1">
              <div v-if="imageData.length <= 0">
                <v-icon> mdi-plus </v-icon>
                <span>صورة المتجر أو العلامة التجارية</span>
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
        </v-col>
        <v-col cols="12" sm="6" md="5" class="pa-0 pa-md-3 pa-lg-3">
          <v-col cols="12" class="pa-2">
            <span class="mb-1 d-inline-block"> أسم المتجر : </span>
            <v-text-field
              v-model="ShowRoomName"
              label="أسم المعرض"
              solo
              hide-details="true"
              max-width="200"
            ></v-text-field>
          </v-col>
          <v-col cols="12" class="pa-2">
            <span class="mb-1 d-inline-block">وصف المتجر :</span>
            <v-textarea
              v-model="ShowRoomName"
              label=" المنطقة"
              solo
              hide-details="true"
              max-width="200"
            ></v-textarea>
          </v-col>
          <v-col cols="12" class="pa-2">
            <v-text-field
              solo
              type="password"
              v-model="password"
              hide-details="true"
              disabled
            ></v-text-field>
            <span class="my-2 d-block" v-text="ShowRoomPassword"> </span>
          </v-col>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "ShowRoomInfoSetting",
  data() {
    return {
      imageData: "",

      ShowRoomName: "معرض النجم للسيارات",
      ShowRoomLocation: "صنعاء-الحوبان-مقابل مدرسة الروضه",
      ShowRoomPassword: "تغير كلمة السر",
      // ShowRoomPassword: "تغير كلمة السر",
      Number1: 1121331731,
      Number2: 1121331732,
      Number3: 1121331733,
      password: "Password",
      show1: false,
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        PasswordMatch: () => `كلمة السر غير صحيحة`,
      },
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
  //  :rules="[rules.required, rules.PasswordMatch]"
  //  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
  //:type="show1 ? 'text' : 'password'"
  //@click:append="show1 = !show1"
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.ShowRoomInfoSetting {
  font-family: $fontfamliy !important;
  letter-spacing: 0px !important;
  color: $fontcolor;
  min-height: 67vh;
  display: flex;
  justify-content: center;
  align-items: center;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
}
::v-deep
  .v-input--selection-controls__input:hover
  .v-input--selection-controls__ripple:before {
  transform: scale(0);
}
::v-deep
  .v-input--selection-controls__input:active
  .v-input--selection-controls__ripple:before {
  transform: scale(0);
}
.image-preview {
  width: 400px;
  height: 400px;
  @media (max-width: 600px) {
    width: 200px;
    height: 200px;
  }
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
    font-size: 12px;
    color: $fontcolorlinks;
    letter-spacing: 0;
    font-weight: 600;
    font-family: $fontfamliy3 !important;
    margin-top: 15px;
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
    max-width: 90%;
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
</style>
