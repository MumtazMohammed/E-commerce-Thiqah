<template>
  <v-app id="inspire">
    <v-app-bar color="grey lighten-2" flat clipped-left app>
      <v-btn icon class="grey lighten-2">
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <v-spacer></v-spacer>
      <v-card-actions class="justify-end">
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      </v-card-actions>
    </v-app-bar>
    <v-navigation-drawer dark v-model="drawer" app clipped stateless>
      <v-sheet color="grey lighten-2" class="pa-3">
        <!-- Company Logo  -->
        <v-card-actions class="justify-center pa-0">
          <v-avatar class="mb-4" color="transparent" size="64">
            <v-img contain src="../assets/outsrc/google.png" />
          </v-avatar>
        </v-card-actions>
      </v-sheet>
      <v-divider></v-divider>
      <v-list rounded>
        <v-list-group>
          <template v-slot:activator>
            <v-list-item-icon>
              <v-icon>mdi-television</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>لوحة القيادة</v-list-item-title>
            </v-list-item-content>
          </template>
          <!-- All the Information  -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'DashBoard',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-content>
              <v-list-item-title> المعلومات حول المعرض</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <!-- Cars  -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'Cars',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-content>
              <v-list-item-title v-text="Messages"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <!-- advertisement -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'Advertisement',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-content>
              <v-list-item-title v-text="advertisement"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <!-- ShowRoomAcount  -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'ShowRoomAccountRequest',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-icon>
              <v-icon> mdi-store-clock-outline </v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="ShowRoomAcount"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <!--  -->
        <v-list-group>
          <template v-slot:activator>
            <v-list-item-icon>
              <v-icon>mdi-account-multiple</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>المسجلين</v-list-item-title>
            </v-list-item-content>
          </template>
          <!-- AllUsers -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'TheUsersAccount',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-content>
              <v-list-item-title v-text="AllUsers"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <!-- AllShowRoom -->
          <v-list-item
            active-class="blue white--text"
            :to="{
              name: 'TheShowRoomAccount',
            }"
            link
            @click="drawer = !drawer"
          >
            <v-list-item-content>
              <v-list-item-title v-text="AllShowRoom"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <!-- Report  -->
        <v-list-item
          active-class="blue white--text"
          :to="{
            name: 'Report',
          }"
          link
          @click="drawer = !drawer"
        >
          <v-list-item-icon>
            <v-icon>mdi-message-reply-text-outline </v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="Report"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <!-- Setting  -->
        <v-list-item
          active-class="blue white--text"
          :to="{
            name: 'AdminSetting',
          }"
          link
          @click="drawer = !drawer"
        >
          <v-list-item-icon>
            <v-icon> mdi-cog-outline </v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="Setting"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <div class="app-route">
        <router-view />
      </div>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: false,
    DashBoard: "لوحة القيادة",
    AllUsers: "المستخدمين",
    AllShowRoom: "المعارض",
    advertisement: "الأعلانات",
    CompanyName: "شركة ثـقــة",
    Report: " البلاغات",
    Messages: "السيارات",
    ShowRoomAcount: "طلب فتح معرض",
    Setting: " الأعدات",
  }),
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.v-list-item__title {
  font-family: $fontfamliy !important;
}
.v-card__title {
  font-family: $fontfamliy !important;
}
.v-application--is-rtl .v-list-item__icon:first-child {
  margin-left: 15px;
}

::v-deep .v-list-item .v-list-item__title {
  line-height: 1.2;
  height: 20px;
}
</style>
