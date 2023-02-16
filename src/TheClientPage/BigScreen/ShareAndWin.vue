<template>
  <div class="Notification">
    <v-container fluid>
      <v-row>
        <v-col cols="3" class="px-md-1 px-lg-1">
          <v-sheet
            v-scroll.self="onScroll"
            class="overflow-y-auto overflow-x-hidden pa-1"
            height="650"
          >
            <v-card flat class="users-card my-1" v-for="n in 20" :key="n">
              <v-card-actions class="pa-0 px-1">
                <v-avatar rounded="" size="30" color="red"> </v-avatar>
                <div>
                  <v-card-title class="pa-0 pr-2 d users-Name text-truncate">
                    محمد أمين شمسان
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
            class="overflow-y-auto overflow-x-hidden pa-1"
            height="600"
            color="grey lighten-2"
          >
            <v-col class="pa-1" cols="12" v-for="n in 8" :key="n">
              <v-card
                flat
                dark
                color="teal darken-1"
                style="width: fit-content; max-width: 250px"
                class="pa-1 message rounded-lg rounded-br-0"
              >
                رسالتيرسالتيرسالتيرسالتيرسالتي رسالتيرسالتيرسالتيرسالتيرسالتي
              </v-card>
            </v-col>
            <v-col class="pa-1" cols="12" v-for="n in 8" :key="n">
              <v-card
                flat
                color="white"
                style="width: fit-content; max-width: 250px; margin-right: auto"
                class="pa-1 message rounded-lg rounded-bl-0"
              >
                رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر رسالة الآخر
                رسالة
              </v-card>
            </v-col>
          </v-sheet>
          <v-card class="mt-2" outlined tile>
            <v-card-actions class="pa-0">
              <v-btn fab small color="transparent" class="elevation-0">
                <v-icon class="grey--text">mdi-emoticon-outline</v-icon>
              </v-btn>
              <v-text-field
                class="elevation-0"
                flat
                placeholder="رسالة"
                dense
                hide-details
                elevation-1
                solo
              ></v-text-field>

              <v-btn fab small color="transparent" class="elevation-0">
                <v-icon class="grey--text">mdi-paperclip</v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
export default {
  components: {},
  name: "Notification",
  data() {
    return {
      scrollInvoked: 0,

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
  }
}
</style>
