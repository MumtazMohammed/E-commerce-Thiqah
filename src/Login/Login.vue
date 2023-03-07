<template>
    <v-main tile flat class="form-box">
        <SystemBar />
        <!-- Logo  -->
        <v-card-actions class="justify-center py-4">
            <h3 class="logo-text">ثــــقـــة لتجارة الأكترونية</h3>
            <v-icon
                style="
                    background-color: #fc624d;
                    padding: 3px;
                    border-radius: 50%;
                    color: white;
                "
                left
                size="28"
                >mdi-shopping</v-icon
            >
        </v-card-actions>
        <!-- Login , sgin up , sgin up as seller -->
        <v-form class="d-flex justify-center form">
            <v-col cols="12" md="8" sm="12" class="px-xs-0">
                <v-card flat color="transparent" class="pa-md-3 pa-lg-3">
                    <!-- Login component -->
                    <v-row
                        justify="center"
                        v-if="
                            SignUpNormalAccount == false &&
                            SignUpSellerAccount == false
                        "
                    >
                        <v-col cols="12">
                            <v-text-field
                                v-model="firstname"
                                label="أسـم الـمستخدم"
                                required
                                hide-details
                                outlined
                                class="red--text"
                                append-icon="far fa-user"
                            ></v-text-field>
                        </v-col>
                        <v-col cols="12" class="pb-0">
                            <v-text-field
                                :append-icon="
                                    show2 ? 'fas fa-eye ' : 'fas fa-eye-slash'
                                "
                                :rules="[rules.required, rules.min]"
                                :type="show2 ? 'text' : 'password'"
                                name="input-10-2"
                                label="كلمة المرور"
                                class="input-group--focused font-weight-regular"
                                @click:append="show2 = !show2"
                                outlined
                                required
                            >
                            </v-text-field>
                        </v-col>
                        <v-col cols="12" class="py-0">
                            <v-card-actions class="justify-center">
                                <v-btn
                                    elevation="0"
                                    min-width="60%"
                                    class="submet"
                                >
                                    تـسجيل الدخول
                                </v-btn>
                            </v-card-actions>
                        </v-col>
                        <v-col cols="12" class="py-0">
                            <v-card-actions class="justify-space-between">
                                <a
                                    large
                                    elevation="0"
                                    min-width="100%"
                                    class="forget"
                                >
                                    هل نسيت كلمة المرور
                                </a>
                            </v-card-actions>
                        </v-col>
                        <v-col cols="6" md="4" sm="4" class="">
                            <v-btn
                                outlined
                                width="100%"
                                class="btn-social"
                                text
                            >
                                جوجل
                                <v-spacer></v-spacer>
                                <v-avatar tile class="mr-2" size="24">
                                    <img
                                        src="../assets/outsrc/google.png"
                                        alt="alt"
                                    />
                                </v-avatar>
                            </v-btn>
                        </v-col>
                        <v-col cols="6" md="4" sm="4" class="">
                            <v-btn
                                outlined
                                width="100%"
                                class="btn-social"
                                text
                            >
                                فيسبوك
                                <v-spacer></v-spacer>
                                <v-avatar tile class="mr-2" size="24">
                                    <img
                                        src="../assets/outsrc/facebook.png"
                                        alt="alt"
                                    />
                                </v-avatar>
                            </v-btn>
                        </v-col>
                    </v-row>
                    <!-- SignUp component -->
                    <v-sheet
                        cols="12"
                        class="pa-0"
                        v-if="SignUpNormalAccount == true"
                    >
                        <SignUp />
                    </v-sheet>
                    <!-- Sign Up as Seller -->
                    <v-sheet
                        cols="12"
                        class="pa-0"
                        v-if="SignUpSellerAccount == true"
                    >
                        <SignUpSeller />
                    </v-sheet>
                    <v-col cols="12" class="">
                        <v-card-actions class="justify-space-around">
                            <a
                                v-if="SignUpSellerAccount == true"
                                @click="
                                    (SignUpNormalAccount = false),
                                        (SignUpSellerAccount = false)
                                "
                                min-width="100%"
                                class="create-new-account"
                            >
                                تسجيل الدخول
                            </a>
                            <a
                                v-else-if="SignUpNormalAccount == true"
                                @click="
                                    (SignUpNormalAccount = false),
                                        (SignUpSellerAccount = false)
                                "
                                min-width="100%"
                                class="create-new-account"
                            >
                                تسجيل الدخول
                            </a>
                            <a
                                v-else
                                @click="
                                    (SignUpNormalAccount =
                                        !SignUpNormalAccount),
                                        (SignUpSellerAccount = false)
                                "
                                min-width="100%"
                                class="create-new-account"
                            >
                                إنشاء حساب جديد
                            </a>
                            <a
                                v-if="SignUpSellerAccount == false"
                                @click="
                                    (SignUpSellerAccount =
                                        !SignUpSellerAccount),
                                        (SignUpNormalAccount = false)
                                "
                                min-width="100%"
                                class="create-new-account"
                            >
                                إنشاء حساب بائع أو مقدم خدمة
                            </a>
                        </v-card-actions>
                    </v-col>
                </v-card>
            </v-col>
        </v-form>
    </v-main>
</template>
<script>
import SignUp from "../Login/SignUp.vue";
import SignUpSeller from "../Login/SignUpSeller.vue";
import SystemBar from "../Login/SystemBar.vue";
// import SignUpSeller from "../Login/SignUpSeller.vue";
export default {
    name: "Login",
    components: { SignUp, SignUpSeller, SystemBar },
    data() {
        return {
            show2: false,
            dialog: false,
            firstname: "",
            SignUpNormalAccount: false,
            SignUpSellerAccount: false,
            rules: {
                required: (value) => !!value || "ادخل الرقم السري",
                min: (v) => v.length >= 8 || "تأكد من ادخال الرقم صحيحا",
            },
        };
    },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";

.form-box {
    min-height: calc(100vh - 40px);
    z-index: 1;
}
.logo-text {
    font-family: $fontfamliy3;
    color: $color-2 !important;
    font-weight: 600 !important;
    font-size: 23px !important;
}

.submet {
    font-family: $fontfamliy3;
    font-size: 16px !important;
    font-weight: 500 !important;
    letter-spacing: 0;
    background-color: $color-2 !important;
    color: $fontcolorsm !important;
    @media (max-width: 600px) {
        font-size: 14px !important;
    }
}

.forget {
    font-family: $fontfamliy3;
    font-size: 13px !important;
    // color: $fontcolorlinks !important;
    letter-spacing: 0;
    transition: all 0.3s ease;
    text-decoration: underline;
}
.create-new-account {
    font-family: $fontfamliy3;
    font-size: 15px !important;
    color: $fontcolorlinks !important;
    letter-spacing: 0;
    text-align: center;
    text-decoration: none;
    display: block;
    @media (max-width: 600px) {
        font-size: 13px !important;
    }
}
// .create-new-account:last-child {
//   font-family: $fontfamliy2;
//   font-size: 15px !important;
//   color: $color-2 !important;
//   letter-spacing: 0;
//   text-align: center;
//   text-decoration: none;
//   display: block;
// }
.btn-social {
    font-family: $fontfamliy3;
    font-size: 15px !important;
    color: $fontcolorlinks !important;
    font-weight: 400 !important;
    letter-spacing: 0;
}
.No-Acount-text {
    font-family: $fontfamliy3;
    font-size: 17px !important;
    font-weight: 500 !important;
    background-color: transparent !important;
    letter-spacing: 0;
    margin-right: 5px;
}
.No-Acount {
    font-family: $fontfamliy3;
    font-size: 14px !important;
    font-weight: 500 !important;
    background-color: transparent !important;
    letter-spacing: 0;
    color: $color-1 !important;
    margin-right: 5px;
}

.or {
    position: relative;
    .text {
        text-align: center;
        background-color: white;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 1;
        padding: 0px 15px;
        display: block;
        font-size: 20px;
    }
}
.or::after {
    content: "";
    position: absolute;
    width: 70%;
    height: 1px;
    background-color: rgb(228, 228, 228);
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 5px;
}
.No-Acount::v-deep.theme--light.v-btn:hover:before {
    opacity: 0;
}
.sign-in-up {
    display: block;
    color: $color-2;
}
.go-back {
    font-size: 17px !important;
    font-weight: 500;
    background-color: transparent !important;
    color: $fontcolorsm !important;
    font-family: $fontfamliy3;
}
.go-back::v-deep.theme--light.v-btn:hover:before {
    opacity: 0;
}
.footer {
    border-top: 1px solid #ffffff;
}
.brand-logo {
    letter-spacing: 0px;
    font-family: $fontfamliy3;
    font-size: 16px;
    font-weight: 300;
}
.brand-Privacy {
    letter-spacing: 0px;
    font-family: $fontfamliy3;
    font-size: 14px;
    display: flex;
    font-weight: 400;
}
::v-deep label.v-label.theme--light {
    font-family: $fontfamliy3 !important;
    font-size: 14px;
    @media (max-width: 600px) {
        font-size: 13px;
    }
}
::v-deep i.v-icon.notranslate.far.fa-user.theme--light {
    font-size: 18px;
}
::v-deep button.v-icon.notranslate.v-icon--link.fas.fa-eye-slash.theme--light {
    font-size: 18px;
}
::v-deep .v-dialog.v-dialog--active {
    @media (max-width: 600px) {
        margin: 1px !important;
    }
}
::v-deep .v-image.v-responsive.theme--light {
    @media (max-width: 600px) {
        max-width: 250px !important;
    }
}
.form {
    @media (max-width: 600px) {
    }
    min-height: calc(100vh - 40px);
    // align-items: center;
}
</style>
