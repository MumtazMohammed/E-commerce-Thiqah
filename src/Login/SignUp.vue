<template>
    <div class="sign-up">
        <v-card
            flat
            color="transparent"
            class="card-con overflow-hidden pa-3"
            ref="form"
        >
            <v-form class="pa-0">
                <v-col class="pa-0 mx-auto" cols="12">
                    <v-text-field
                        ref="FirstName"
                        v-model="FirstName"
                        :rules="[() => !!FirstName || 'This field is required']"
                        :error-messages="errorMessages"
                        label="الأسم كامل"
                        required
                        outlined
                    ></v-text-field>
                </v-col>
                <v-col class="pa-0 mx-auto" cols="12">
                    <v-text-field
                        ref="number"
                        v-model="number"
                        :rules="[() => !!number || 'This field is required']"
                        label="جوال"
                        :error-messages="errorMessages"
                        required
                        outlined
                        class="ma-0"
                    ></v-text-field>
                </v-col>
                <v-col class="pa-0 mx-auto" cols="12">
                    <v-text-field
                        :rules="[rules.required, rules.min]"
                        :type="show2 ? 'text' : 'password'"
                        v-model="password"
                        label="كلمة المرور"
                        class="input-group--focused ma-0 font-weight-regular"
                        outlined
                        required
                    >
                    </v-text-field>
                </v-col>
                <v-col cols="12" class="pa-0">
                    <v-switch
                        v-model="show2"
                        @click:append="show2 = !show2"
                        :type="show2 ? 'text' : 'password'"
                        color="info"
                        hide-details
                        label="  اظهار كلمة المرور"
                        class="ma-0 switch"
                    >
                    </v-switch>
                </v-col>
                <v-col cols="12" class="pt-0">
                    <v-card-actions class="justify-center pa-4">
                        <v-btn class="btn1 elevation-0" @click="submit">
                            انشاء
                        </v-btn>
                    </v-card-actions>
                </v-col>
            </v-form>
        </v-card>
    </div>
</template>
<script>
export default {
    components: {},
    name: "SginUp",
    data: () => ({
        errorMessages: "",
        FirstName: "",
        number: "",
        password: "",
        show2: false,
        formHasErrors: false,
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
    font-family: $fontfamliy;

    .showPassLab {
        font-family: $fontfamliy2;
        font-size: 15px;
        letter-spacing: 0;
        color: $fontcolorlinks;
        @media (max-width: 600px) {
            font-size: 13px;
        }
    }
    .btn1 {
        color: $fontcolorsm;
        letter-spacing: 0;
        font-family: $fontfamliy;
        width: 250px;
        font-size: 18px;
        background: $color-2 !important;
    }

    .switch::v-deep
        .v-input--selection-controls__input:hover
        .v-input--selection-controls__ripple:before {
        transform: scale(0);
    }
}
</style>
