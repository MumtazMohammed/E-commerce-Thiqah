<template>
    <div class="sign-up">
        <v-stepper v-model="e1">
            <v-stepper-header>
                <v-stepper-step :complete="e1 > 1" step="1">
                    معلومات البائع
                </v-stepper-step>
                <v-divider></v-divider>
                <v-stepper-step :complete="e1 > 2" step="2">
                    معلومات المتجر
                </v-stepper-step>
                <v-divider></v-divider>
                <v-stepper-step :complete="e1 > 3" step="3">
                    تأكيد
                </v-stepper-step>
                <v-divider></v-divider>
                <v-stepper-step :complete="e1 > 4" step="4">
                    إرسال
                </v-stepper-step>
            </v-stepper-header>
            <v-stepper-items>
                <v-stepper-content step="1">
                    <v-card
                        tile
                        flat
                        class="pa-0 pa-xs-0"
                        color="transparent"
                        height="auto"
                    >
                        <v-row>
                            <v-col class="pb-0" cols="12">
                                <v-radio-group
                                    hide-details
                                    row
                                    v-model="radios"
                                >
                                    <template v-slot:label>
                                        <strong>نوع البائع </strong>
                                    </template>
                                    <v-radio value="أفراد">
                                        <template v-slot:label>
                                            <div>أفراد</div>
                                        </template>
                                    </v-radio>
                                    <v-radio value="شركة">
                                        <template v-slot:label>
                                            <div>شركة مسجلة</div>
                                        </template>
                                    </v-radio>
                                </v-radio-group>
                            </v-col>
                            <!-- individual -->
                            <v-col
                                v-if="radios === 'أفراد'"
                                class="mx-auto pb-0"
                                cols="12"
                            >
                                <v-text-field
                                    ref="FirstName"
                                    v-model="FirstName"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label="الأسم كامل"
                                    required
                                    dense
                                    outlined
                                ></v-text-field>
                            </v-col>
                            <v-col
                                v-if="radios === 'أفراد'"
                                class="mx-auto py-0"
                                cols="12"
                            >
                                <v-text-field
                                    dense
                                    ref="FirstName"
                                    v-model="IcNo"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label=" رقم البطاقة / رقم جواز السفر"
                                    required
                                    outlined
                                ></v-text-field>
                            </v-col>
                            <!-- company -->
                            <v-col
                                v-if="radios === 'شركة'"
                                class="mx-auto pb-0"
                                cols="12"
                            >
                                <v-text-field
                                    ref="FirstName"
                                    v-model="CompanyName"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label="أسم الشركة "
                                    required
                                    dense
                                    outlined
                                ></v-text-field>
                            </v-col>
                            <v-col
                                v-if="radios === 'شركة'"
                                class="mx-auto py-0"
                                cols="12"
                            >
                                <v-text-field
                                    dense
                                    ref="FirstName"
                                    v-model="CompanyNo"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label="رقم السجل التجاري"
                                    required
                                    outlined
                                ></v-text-field>
                            </v-col>
                        </v-row>
                    </v-card>
                    <v-divider class="my-3"></v-divider>
                    <v-card-actions>
                        <v-btn
                            elevation="0"
                            small
                            class="btn1"
                            color="primary"
                            @click="e1 = 2"
                        >
                            التالي
                        </v-btn>
                    </v-card-actions>
                </v-stepper-content>

                <v-stepper-content step="2">
                    <v-card
                        tile
                        flat
                        class="pa-2"
                        color="transparent"
                        height="auto"
                    >
                        <v-row>
                            <v-col class="mx-auto pb-0" cols="12">
                                <v-text-field
                                    ref="FirstName"
                                    v-model="ShopeName"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label="أسم المتجر "
                                    required
                                    dense
                                    outlined
                                ></v-text-field>
                            </v-col>
                            <v-col class="mx-auto py-0" cols="12">
                                <v-textarea
                                    ref="FirstName"
                                    v-model="Address"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label=" عنوان المتجر   "
                                    required
                                    outlined
                                ></v-textarea>
                            </v-col>
                            <v-col class="mx-auto py-0" cols="12">
                                <v-text-field
                                    ref="FirstName"
                                    v-model="Email"
                                    :rules="[
                                        () =>
                                            !!FirstName || 'هذه الخانة مطلوبه',
                                    ]"
                                    :error-messages="errorMessages"
                                    label="البريد الأكترواني"
                                    required
                                    outlined
                                ></v-text-field>
                            </v-col>
                            <v-col class="mx-auto py-0" cols="12">
                                <v-text-field
                                    ref="number"
                                    v-model="PhoneNumber"
                                    :rules="[
                                        () => !!number || 'هذه الخانة مطلوبه',
                                    ]"
                                    label="جوال"
                                    :error-messages="errorMessages"
                                    required
                                    outlined
                                    class="ma-0"
                                ></v-text-field>
                            </v-col>
                        </v-row>
                    </v-card>

                    <v-divider class="my-3"></v-divider>
                    <v-card-actions class="justify-space-between">
                        <v-btn small elevation="0" class="btn1" @click="e1 = 3">
                            التالي
                        </v-btn>
                        <v-btn small class="btn1" text @click="e1 = 1">
                            رجوع
                        </v-btn>
                    </v-card-actions>
                </v-stepper-content>
                <v-stepper-content step="3">
                    <v-card flat class="" color="transparent">
                        <v-card-text class="pa-1">
                            <strong class="ml-2">نوع العميل :</strong>
                            {{ radios }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1">أسم الشركة / العميل :</strong>
                            {{ FirstName }}
                            {{ CompanyName }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1"
                                >رقم الشركة / رقم البطاقة أو جواز السفر :
                            </strong>
                            {{ IcNo }}
                            {{ CompanyNo }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1">أسم المتجر :</strong>
                            {{ ShopeName }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1">العنوان :</strong>
                            {{ Address }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1">البريد الأكتروني :</strong>
                            {{ Email }}
                        </v-card-text>
                        <v-card-text class="pa-1">
                            <strong class="ml-1">رقم الجوال :</strong>
                            {{ PhoneNumber }}
                        </v-card-text>
                    </v-card>
                    <v-divider class="my-3"></v-divider>
                    <v-card-actions class="justify-space-between">
                        <v-btn small elevation="0" class="btn1" @click="e1 = 4">
                            إرسال الطلب
                        </v-btn>
                        <v-btn small class="btn1" text @click="e1 = 2">
                            رجوع
                        </v-btn>
                    </v-card-actions>
                </v-stepper-content>
                <v-stepper-content step="4">
                    <v-card flat class="" color="transparent">
                        <v-card-text class="text-center submit">
                            تم إرسال طلبك بنجاح سيتم مراجعة طلبك والتواصل معكم
                            بإقرب وقت
                        </v-card-text>
                    </v-card>
                </v-stepper-content>
            </v-stepper-items>
        </v-stepper>
    </div>
</template>
<script>
export default {
    components: {},
    name: "SginUp",
    data: () => ({
        FirstName: "",
        CompanyName: "",
        errorMessages: "",
        IcNo: "",
        CompanyNo: "",
        ShopeName: "",
        Address: "",
        PhoneNumber: "",
        Email: "",
        radios: "أفراد",
        show2: false,
        e1: 1,
        formHasErrors: false,
        select: ["تاجر"],
        dropdown: [{ text: "تاجر" }, { text: "وكيل" }],

        emailRules: [
            (v) => !!v || "يجب ادخل الـبريد الأكتروني ",
            (v) => /.+@.+/.test(v) || "يـجب كتابة البريد الأكتروني صحيحا",
        ],
        rules: {
            required: (value) => !!value || "ادخل الرقم السري",
            min: (v) => v.length >= 8 || "تأكد من ادخال الرقم صحيحا",
        },
    }),

    computed: {
        form() {
            return {
                FirstName: this.name,
                SecondtName: this.name,
                country: this.country,
                email: this.country,
                number: this.Number,
                doublepassword: this.Number,
                password: this.Number,
            };
        },
    },
    watch: {
        FirstName() {
            this.errorMessages = "";
        },
        SecondtName() {
            this.errorMessages = "";
        },
        country() {
            this.errorMessages = "";
        },
        email() {
            this.errorMessages = "";
        },
        Number() {
            this.errorMessages = "";
        },
    },

    methods: {
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

.sign-up {
    width: 100%;
    font-family: $fontfamliy3;
    letter-spacing: 0 !important;
    .card-con {
        position: relative;
        background-color: rgb(255, 255, 255) !important;
    }
    .showPassLab {
        font-family: $fontfamliy3;
        font-size: 16px;
    }
    .btn1 {
        letter-spacing: 0;
        font-family: $fontfamliy3;
        font-size: 14px;
        background-color: $color-2 !important;
        color: #fff;
    }

    .switch::v-deep
        .v-input--selection-controls__input:hover
        .v-input--selection-controls__ripple:before {
        transform: scale(0);
    }
    ::v-deep .v-card__text.pa-1 {
        letter-spacing: 0 !important;
        font-size: 16px !important;
        color: #43a047;
    }
    strong {
        letter-spacing: 0 !important;
        color: $fontcolorlinks !important;
        font-size: 14px !important;
    }
    .submit {
        letter-spacing: 0 !important;
        color: $fontcolorlinks !important;
        font-size: 16px !important;
    }
}
</style>
