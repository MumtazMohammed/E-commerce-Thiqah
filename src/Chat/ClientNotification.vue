<template>
  <div class="Notification">
    <v-badge left bordered color="error" icon="mdi-lock" overlap>
      <v-btn
        large
        @click.stop="chat = true"
        class="white--text open-message"
        color="error"
        depressed
      >
        الدردشه
        <v-icon right>mdi-forum-outline</v-icon>
      </v-btn>
    </v-badge>

    <v-dialog max-width="900" v-model="chat" inset persistent>
      <v-sheet>
        <v-toolbar flat dense color="grey lighten-2">
          <v-toolbar-title class="open-message"> الدردشة </v-toolbar-title>
          <v-spacer></v-spacer>
          <v-btn @click.stop="chat = false" icon>
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-toolbar>
        <v-row no-gutters class="">
          <v-col cols="4" class="px-md-1 px-lg-1">
            <v-sheet
              v-scroll.self="onScroll"
              class="overflow-y-auto overflow-x-hidden"
              height="550"
              style="border-left: 1px solid #e0e0e0"
            >
              <v-banner color="white" sticky>
                <v-text-field
                  placeholder="أبحث عن مستخدم"
                  hide-details
                  dense
                  filled
                >
                </v-text-field>
              </v-banner>
              <v-card flat class="users-card my-1" v-for="n in 20" :key="n">
                <v-card-actions class="pa-0 px-1">
                  <v-avatar rounded="" size="30" color="red"> </v-avatar>
                  <div>
                    <v-card-title class="pa-0 pr-2 d users-Name text-truncate">
                      محمد أمين
                    </v-card-title>
                    <v-card-text
                      class="pa-0 pr-2 users-Message text--disabled text-truncate"
                    >
                      محمد أمين شمسان
                    </v-card-text>
                  </div>
                  <v-spacer></v-spacer>
                  <span class="unred-message">5</span>
                </v-card-actions>
              </v-card>
            </v-sheet>
          </v-col>
          <v-col class="px-md-1 px-lg-1">
            <v-sheet
              v-scroll.self="onScroll"
              class="overflow-y-auto overflow-x-hidden"
              height="440"
            >
              <v-banner color="white" sticky>
                <v-menu rounded="0" left offset-y>
                  <template v-slot:activator="{ attrs, on }">
                    <v-btn
                      color="grey"
                      class="white--text message"
                      v-bind="attrs"
                      v-on="on"
                      small
                    >
                      اسم المستخدم
                      <v-icon right>mdi-chevron-down</v-icon>
                    </v-btn>
                  </template>
                  <v-list>
                    <v-list-item link>
                      <v-list-item-title class="user-option">
                        <v-icon size="17" right>mdi-account</v-icon>
                        عرض الصفحة الشخصية
                      </v-list-item-title>
                    </v-list-item>
                    <v-list-item link>
                      <v-list-item-title class="user-option">
                        <v-icon size="17" right>mdi-block-helper</v-icon>
                        حظر المستخدم
                      </v-list-item-title>
                    </v-list-item>
                  </v-list>
                </v-menu>
              </v-banner>
              <v-col class="pa-1" cols="12" v-for="n in 8" :key="n">
                <v-card
                  flat
                  dark
                  color="blue lighten-3"
                  style="width: fit-content; max-width: 250px"
                  class="pa-1 message rounded-lg rounded-br-0"
                >
                  رسالتيرسالتيرسالتيرسالتيرسالتي رسالتيرسالتيرسالتيرسالتيرسالتي
                </v-card>
              </v-col>
              <v-col class="pa-1" cols="12" v-for="n in 8" :key="n">
                <v-card
                  flat
                  color="grey lighten-2"
                  style="
                    width: fit-content;
                    max-width: 250px;
                    margin-right: auto;
                  "
                  class="pa-1 message rounded-lg rounded-bl-0"
                >
                  رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر
                  رسالة
                </v-card>
              </v-col>
            </v-sheet>
            <!-- <v-btn fab small color="transparent" class="elevation-0">
                    <v-icon class="grey--text">mdi-emoticon-outline</v-icon>
                  </v-btn> -->
            <v-divider class="my-2"></v-divider>
            <v-textarea
              class="elevation-0 rounded-0"
              flat
              placeholder=" أكتب رسالتك هنا ..."
              dense
              hide-details
              solo
              no-resize
              rows="2"
            ></v-textarea>
            <v-row class="px-2" no-gutters>
              <v-icon class="blue--text">mdi-emoticon-outline</v-icon>
              <v-icon class="blue--text">mdi-image</v-icon>
            </v-row>
            <!-- <v-btn fab small color="transparent" class="elevation-0">
                    <v-icon class="grey--text">mdi-paperclip</v-icon>
                  </v-btn> -->
          </v-col>
        </v-row>
      </v-sheet>
    </v-dialog>
  </div>
</template>
<script>
export default {
  components: {},
  name: "Notification",
  data() {
    return {
      scrollInvoked: 0,
      chat: false,
      items: [
        {
          color: "#1F7087",
          src: "https://cdn.vuetifyjs.com/images/cards/foster.jpg",
          title: "Supermodel",
          artist: "Foster the People",
        },
        {
          color: "#952175",
          src: "https://cdn.vuetifyjs.com/images/cards/halcyon.png",
          title: "Halcyon Days",
          artist: "Ellie Goulding",
        },
      ],
    };
  },
  methods: {
    onScroll() {
      this.scrollInvoked++;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Notification {
  width: 100%;
  // padding: $padding;
  position: fixed;
  bottom: 5px;
  z-index: 50;
  right: 13px;
}
.users-card:hover {
  background-color: #eee;
}
.users-Name {
  font-size: 13px !important;
  font-family: $fontfamliy3;
  // width: 100px;
}
.users-Message {
  font-size: 12px !important;
  font-family: $fontfamliy3;
  display: block !important;
}
.unred-message {
  width: 30px;
  height: 17px;
  background-color: $color-2;
  color: #fff;
  border-radius: 5px;
  font-size: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.message {
  // font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 13.5px;
  text-align: start;
  line-height: 1.5;
  color: $fontcolor !important;
}
.open-message {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 20px !important;
  font-weight: 500;
}
::v-deep textarea::placeholder {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 15px !important;
}
::v-deep input::placeholder {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 13px !important;
}
::v-deep .v-banner__wrapper {
  padding: 5px !important;
}
.user-option {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 13px !important;
}
</style>
