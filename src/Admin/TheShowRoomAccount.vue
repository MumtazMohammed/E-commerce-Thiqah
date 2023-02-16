<template>
  <div class="TheShowRoomAccount">
    <v-container>
      <v-card-title class="justify-center text" v-text="ShowroomTitle">
      </v-card-title>
      <!-- search for showroom -->
      <v-row no-gutters class="justify-center">
        <v-card flat outlined class="search-card overflow-hidden" width="500">
          <!-- delete text  -->
          <v-btn
            v-if="search.length > 0 && ShowSerachCardvisble"
            small
            icon
            color="white"
            class="mr-1 red darken-1"
            @click="reset()"
          >
            <v-icon class="">mdi-close</v-icon>
          </v-btn>
          <!-- customiza search -->
          <v-text-field
            class="rounded-b-0"
            v-model="search"
            solo
            large
            flat
            label="أبحث عن معرض ؟"
            hide-details="true"
            background-color="#fff"
            append-icon="mdi-store-search-outline"
          ></v-text-field>
        </v-card>
      </v-row>
      <!--end search  -->
      <v-row>
        <v-col cols="12" sm="4" md="3">
          <v-select
            :items="items"
            label="فلتر المعارض "
            v-model="value"
            outlined
            hide-details="true"
            color="indigo"
          ></v-select>
        </v-col>
        <v-col cols="12" sm="4" md="3">
          <v-select
            :items="RentShowRoom"
            label="فلتر الأيجار الشهري "
            outlined
            hide-details="true"
            color="indigo"
          ></v-select>
        </v-col>
      </v-row>
      <v-card
        to="/ShowRoomPageInfo"
        v-for="(showroom, i) in filteredStore"
        :key="i"
        class="pa-2 my-3"
        :class="showroom.featured == true ? 'card-featured' : 'card'"
      >
        <v-row class="justify-center">
          <v-col cols="4" md="1" sm="1" class="mx-auto">
            <v-card-actions class="justify-center">
              <v-avatar size="30" color="transparent">
                <img
                  :src="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                  :alt="getimageUrl(showroom.folder, showroom.ShowroomImg)"
                />
              </v-avatar>
            </v-card-actions>
          </v-col>
          <v-col cols="8" md="3" sm="3" class="my-auto">
            <v-card-text
              class="py-0 text-center"
              v-text="showroom.ShowroomName"
            >
            </v-card-text>
          </v-col>
          <v-col cols="6" md="2" sm="2" class="my-auto">
            <v-card-text class="py-0 text-center" v-text="showroom.location">
            </v-card-text>
          </v-col>
          <v-col cols="6" md="2" sm="2" class="my-auto">
            <v-card-text class="py-0 text-center">
              <span>80</span>
              سيارة
            </v-card-text>
          </v-col>
          <v-col cols="6" md="2" sm="2" class="my-auto">
            <v-card-text class="py-0 text-center"> 25/05/2022</v-card-text>
          </v-col>
          <v-col cols="6" md="2" sm="2" class="my-auto">
            <span class="running text-center">30</span>
            <v-card-text class="py-0 text-center"> يوم</v-card-text>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>
<script>
import showrooms from "../data-json/showroom.json";
export default {
  name: "TablesInfo",
  data() {
    return {
      showrooms,
      ShowroomTitle: "المعارض",
      search: "",
      ShowSerachCard: "",
      value: "الكل",
      items: ["الكل", "المعارض المتميز", "المعارض غير المتميز"],
      RentShowRoom: ["أقل من 25 يوم", "أقل من 15 يوم", "أقل من 10 يوم"],
    };
  },
  methods: {
    getimageUrl(FolderName, ImageName) {
      let image = require.context("@/assets/");
      return image("./" + FolderName + "/" + ImageName);
    },
    reset() {
      return (this.search = "");
    },
  },
  computed: {
    filteredStore: function () {
      return this.showrooms.filter((showroom) => {
        return showroom.ShowroomName.match(this.search);
      });
    },

    length() {
      return 7000;
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheShowRoomAccount {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  width: 100%;
  min-height: 100vh;
  padding: $padding;
}
::v-deep .v-list-item .v-list-item__title {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
.feature-btn {
  font-family: $fontfamliy;
  letter-spacing: 0px;
  font-size: 14px;
}
.text {
  font-family: $fontfamliy;
  letter-spacing: 0px;
}
.running {
  display: block;
  color: green;
}
.card {
  position: relative;
  overflow: hidden;
}
.card::after {
  content: "";
  position: absolute;
  height: 100%;
  width: 5px;
  top: 0;
  right: 0;
  background-color: #66666672;
  box-shadow: 2px 0px 0px 0px #66666672 !important;
}
.card-featured {
  position: relative;
  overflow: hidden;
}
.card-featured::after {
  content: "";
  position: absolute;
  height: 100%;
  width: 5px;
  top: 0;
  right: 0;
  background-color: #42a4f587;
  box-shadow: 2px 0px 0px 0px #66666672 !important;
}
.user-card {
  border: 1px solid rgba(128, 128, 128, 0.429) !important;
  border-radius: 10px !important;
}
</style>
