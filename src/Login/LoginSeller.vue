<template>
    <div>
        <v-toolbar color="#293043" class="px-md-14 px-lg-14">
            <router-link class="NavTitle" router to="/">
                <a class="NavTitle"> ثــقـة </a>
            </router-link>
            <v-spacer></v-spacer>
            <v-card-actions>
                <v-card-text
                    class="grey--text pa-0 No-Acount-text"
                    v-if="SignUp == false"
                >
                    فتح حساب تاجر / وكيل ؟
                    <v-btn
                        @click="SignUp = true"
                        elevation="0"
                        class="No-Acount px-0"
                    >
                        أفتح حساب
                    </v-btn>
                </v-card-text>
                <v-btn
                    v-else
                    @click="SignUp = false"
                    elevation="0"
                    class="go-back px-0"
                >
                    <v-icon right class="mt-2">mdi-chevron-right</v-icon>
                    رجوع
                </v-btn>
            </v-card-actions>
        </v-toolbar>
        <div class="LoginSeller">
            <v-container>
                <v-card flat class="pa-2 pb-5 mx-auto" width="600">
                    <v-card-title class="sign-creat">
                        <span
                            v-bind:class="{
                                'sign-in-up': SignUp == false,
                            }"
                            class="mx-2"
                        >
                            تسجيل الدخول
                        </span>
                        /
                        <span
                            v-bind:class="{
                                'sign-in-up': SignUp == true,
                            }"
                            class="mx-2"
                        >
                            فتح حساب
                        </span>
                    </v-card-title>
                    <v-form>
                        <div v-if="SignUp == false">
                            <v-row justify="center">
                                <v-col cols="12">
                                    <v-text-field
                                        v-model="firstname"
                                        label=" الرقم التعريفي"
                                        required
                                        hide-details
                                        outlined
                                        class="red--text field"
                                        append-icon="far fa-user"
                                    ></v-text-field>
                                </v-col>
                                <v-col cols="12" class="pb-0">
                                    <v-text-field
                                        :append-icon="
                                            show2
                                                ? 'fas fa-eye '
                                                : 'fas fa-eye-slash'
                                        "
                                        :rules="[rules.required, rules.min]"
                                        :type="show2 ? 'text' : 'password'"
                                        name="input-10-2"
                                        label="كلمة المرور"
                                        class="input-group--focused font-weight-regular field"
                                        @click:append="show2 = !show2"
                                        outlined
                                        required
                                    >
                                    </v-text-field>
                                </v-col>
                                <v-col cols="12" class="pa-0">
                                    <v-card-actions class="justify-center">
                                        <v-btn
                                            dark
                                            large
                                            color="#0881fa"
                                            elevation="0"
                                            min-width="270px"
                                            class="submet"
                                        >
                                            تـسجيل الدخول</v-btn
                                        >
                                    </v-card-actions>
                                </v-col>
                                <v-col
                                    cols="12"
                                    class="pa-2 d-flex justify-center"
                                >
                                    <v-card-actions class="pa-0">
                                        <a class="forget"
                                            >هل نسيت كلمة المرور</a
                                        >
                                    </v-card-actions>
                                </v-col>
                            </v-row>
                        </div>
                        <div v-else>
                            <SignUpSeller />
                        </div>
                    </v-form>
                </v-card>
            </v-container>
        </div>
        <!-- footer  -->
        <v-row>
            <v-col cols="12">
                <v-footer class="footer" padless>
                    <v-card color="#293043" class="flex" flat tile>
                        <v-card-actions
                            color="transparent"
                            class="pa-4 justify-center justify-lg-space-between justify-md-space-between flex-wrap"
                        >
                            <v-card-title>
                                <router-link
                                    :to="{
                                        name: 'TheTerms',
                                        params: { Terms: ' الأحكام والشروط' },
                                    }"
                                    class="mx-2 brand-Privacy grey--text text--darken-1"
                                >
                                    <a> الأحكام والشروط </a>
                                </router-link>
                                <span class="grey--text">|</span>
                                <router-link
                                    :to="{
                                        name: 'ThePrivacy',
                                        params: { Privacy: ' سياسة الخصوصية' },
                                    }"
                                    class="mx-2 brand-Privacy grey--text text--darken-1"
                                >
                                    <a> سياسة الخصوصية </a>
                                </router-link>
                            </v-card-title>
                            <p
                                class="pa-4 ma-0 grey--text text-end brand-logo text--lighten-1"
                            >
                                <strong class="ml-2">
                                    &COPY; جميع الحقوق محفوظة لشركة ثـقـــة
                                </strong>
                                2022 —
                                {{ new Date().getFullYear() }}
                            </p>
                        </v-card-actions>
                    </v-card>
                </v-footer>
            </v-col>
        </v-row>
    </div>
</template>
<script>
import SignUpSeller from "./SignUpSeller.vue";
export default {
    name: "LoginSeller",
    components: { SignUpSeller },
    data() {
        return {
            props: ["dialog"],
            SignUp: false,
            valid: false,
            firstname: "",
            show2: false,
            rules: {
                required: (value) => !!value || "ادخل الرقم السري",
                min: (v) => v.length >= 8 || "تأكد من ادخال الرقم صحيحا",
            },
        };
    },
    methods: {
        closedialog(event) {
            this.dia = event.target.value;
            this.$emit("dialogclose", this.dia);
        },
    },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
.LoginSeller {
    width: 100%;
    min-height: 78vh;
    font-family: $fontfamliy;
    background-color: #374255;
    padding: $padding;
    @include flexcenter();
    .field {
        font-family: $fontfamliy;
        letter-spacing: 0;
    }
    .sign-creat {
        font-family: $fontfamliy;
        font-weight: 500 !important;
        letter-spacing: 0;
        @media (max-width: 360px) {
            font-size: 16px !important;
        }
    }
}
.NavTitle {
    color: $fontcolorsm !important;
    font-size: 22px;
    letter-spacing: 0px !important;
    font-family: $fontfamliy;
    font-weight: 500;
    width: fit-content;
    text-align: start;
    text-decoration: none !important;
}
.submet {
    font-family: $fontfamliy;
    letter-spacing: 0;
    font-size: 18px !important;
}
.forget {
    font-family: $fontfamliy;
    font-size: 16px;
    font-weight: 300 !important;

    @media (max-width: 400px) {
        font-size: 14px;
    }
    @media (max-width: 300px) {
        font-size: 12px;
    }
}
.sign-in-up {
    display: block;
    color: $color-1;
}
.go-back {
    font-size: 17px !important;
    font-weight: 500;
    background-color: transparent !important;
    color: $fontcolorsm !important;
    font-family: $fontfamliy;
}
.No-Acount-text {
    font-family: $fontfamliy;
    font-size: 17px !important;
    font-weight: 500 !important;
    background-color: transparent !important;
    letter-spacing: 0;
    margin-right: 5px;
}
.No-Acount {
    font-family: $fontfamliy !important;
    font-size: 14px !important;
    font-weight: 500 !important;
    background-color: transparent !important;
    letter-spacing: 0;
    color: $color-1 !important;
    margin-right: 5px;
}
.footer {
    border-top: 1px solid #ffffff;
}
.brand-logo {
    letter-spacing: 0px;
    font-family: $fontfamliy;
    font-size: 16px;
    font-weight: 300;
}
.brand-Privacy {
    letter-spacing: 0px;
    font-family: $fontfamliy;
    font-size: 14px;
    display: flex;
    font-weight: 400;
}
</style>
