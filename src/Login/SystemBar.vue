<template>
    <v-system-bar height="40px" color="#eee">
        <v-card tile flat color="transparent" to="/" class="btn1 mx-1">
            <v-card-actions class="pa-0">
                <v-icon dark class="icon" right>mdi-home</v-icon>
                <v-card-text v-text="btnSignUp" class="sgin pa-0"></v-card-text>
                <!-- <v-icon class="sign-in-icon" right>mdi-account</v-icon> -->
            </v-card-actions>
        </v-card>
        <!-- Be a personal seller or company  -->
        <v-card tile flat color="transparent" class="btn1 mx-1">
            <v-card-actions class="pa-0">
                <v-icon dark class="icon" right>mdi-help</v-icon>
                <v-card-text v-text="Help" class="sgin pa-0"></v-card-text>
                <!-- <v-icon class="sign-in-icon" right>mdi-account</v-icon> -->
            </v-card-actions>
        </v-card>
        <!-- Be a personal seller or company  -->
        <v-card tile flat color="transparent" class="btn1 mx-1">
            <v-card-actions class="pa-0">
                <v-icon dark right class="icon">mdi-text-box-outline</v-icon>
                <v-card-text v-text="AboutWeb" class="sgin pa-0"></v-card-text>
                <!-- <v-icon class="sign-in-icon" right>mdi-account</v-icon> -->
            </v-card-actions>
        </v-card>
    </v-system-bar>
    <!-- Be a personal seller or company  -->

    <!-------------------------->
</template>
<script>
export default {
    name: "LogingAndSignup",
    data() {
        return {
            btnSignUp: "الرئيسية",
            Help: "مساعدة",
            AboutWeb: "الشروط والأحكام",
            Login: [
                { title: " تسجيل أفراد", path: "/Login" },
                { title: "تسجيل شركات ", path: "/LoginSeller" },
            ],
        };
    },
};
</script>
<style lang="scss" scoped>
@import "../scss/virables";
@import "../scss/mixin";
.hidden {
    .user {
        @media (max-width: 600px) {
            display: flex;
            flex-direction: column-reverse;
            justify-content: center;
            align-items: center;
        }
    }
    b {
        font-size: 14px;
        @media (max-width: 600px) {
            color: $fontcolorsm !important;
        }
    }

    .icon {
        font-size: 18px !important;
    }
    .btn1 {
        cursor: pointer;
        font-size: 13px;
        @media (max-width: 959px) {
            background: transparent !important;
            color: $fontcolor !important;
        }
        .icon {
            font-size: 18px;
            color: $fontcolorsm !important;
        }
        .sgin {
            color: $fontcolorsm !important;
            letter-spacing: 0px;
            font-family: $fontfamliy3;
            font-size: 12.5px;
            font-weight: 500 !important;
        }
    }
}
.title-link {
    font-family: $fontfamliy2 !important;
    font-size: 13px !important;
    font-weight: 400;
}
.title-link-box {
    transition: all 0.3s ease;
}
.title-link-box:hover {
    color: $color-1 !important;
}
::v-deep .v-list.v-sheet.theme--light {
    padding: 0 !important;
}
::v-deep .v-list-item {
    min-height: 35px !important;
}
::v-deep a#list-item-640 {
    min-height: 35px !important;
}
.show-menu-icon {
    position: absolute !important;
    right: 0;
    bottom: 0px;
}
::v-deep hr.mx-2.white.v-divider.v-divider--vertical.theme--light {
    height: 27px !important;
}
</style>
