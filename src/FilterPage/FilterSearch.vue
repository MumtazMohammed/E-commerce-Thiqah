<template>
  <div>
    <!-- fillter small screen from 960px and down -->
    <div class="hidden-md-and-up filtertion">
      <v-btn-toggle dense style="width: 100%" group v-model="toggle_none">
        <!-- price  -->
        <v-menu v-model="price" class="py-0" bottom left offset-y open-on-click>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              width="25%"
              class="filtertion-btn ma-0"
              v-bind="attrs"
              v-on="on"
              large
            >
              السعر
              <v-icon
                right
                v-text="price ? 'mdi-menu-up' : 'mdi-menu-down'"
              ></v-icon>
            </v-btn>
          </template>
          <v-list class="py-0">
            <v-list-item>
              <v-icon size="23" color="light-blue" right>
                mdi-swap-vertical
              </v-icon>
              <v-list-item-title class="filtertion-list">
                من أعلى سعر الى أقل سعر
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-icon size="23" color="light-blue" right>
                mdi-swap-vertical mdi-flip-h
              </v-icon>
              <v-list-item-title class="filtertion-list">
                من أقل سعر الى أعلى سعر
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <!-- location  -->
        <v-menu v-model="location" bottom left offset-y open-on-click>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              width="25%"
              class="filtertion-btn ma-0"
              v-bind="attrs"
              v-on="on"
              large
            >
              المنطقة
              <v-icon
                right
                v-text="location ? 'mdi-menu-up' : 'mdi-menu-down'"
              ></v-icon>
            </v-btn>
          </template>
          <v-list class="py-0">
            <v-card-actions class="justify-center">
              <v-chip label class="filtertion-list">
                <v-icon size="20" color="light-blue" left>
                  mdi-map-marker-radius
                </v-icon>
                حدد موقعي
              </v-chip>
            </v-card-actions>
            <v-sheet
              color="grey lighten-4"
              max-height="200"
              min-height="150"
              style="overflow-y: scroll"
            >
              <v-chip-group column class="justify-center">
                <v-chip
                  filter
                  color="grey lighten-2"
                  v-for="i in 50"
                  :key="i"
                  label
                  class="filtertion-list ma-1"
                >
                  تعز
                </v-chip>
              </v-chip-group>
            </v-sheet>
          </v-list>
        </v-menu>
        <!-- condtion -->
        <v-menu v-model="condtion" bottom left offset-y open-on-click>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              width="25%"
              class="filtertion-btn ma-0"
              v-bind="attrs"
              v-on="on"
              large
            >
              الحالة
              <v-icon
                right
                v-text="condtion ? 'mdi-menu-up' : 'mdi-menu-down'"
              ></v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-list-item-title class="filtertion-list">
                الكل
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title class="filtertion-list">
                جديد
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title class="filtertion-list">
                مستعمل
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-btn
          width="25%"
          class="filtertion-btn ma-0"
          @click="(drawer = !drawer), filter == false"
          elevation="0"
          large
        >
          فلتر
          <v-icon right>mdi-filter-variant</v-icon>
        </v-btn>
      </v-btn-toggle>
      <v-navigation-drawer v-model="drawer" app right hide-overlay>
        <v-sheet color="white">
          <v-card class="pa-2" tile flat>
            <div>
              <v-card-text class="pa-2 text"> المناطق </v-card-text>
              <v-row no-gutters>
                <v-col class="" cols="12">
                  <v-chip-group column multiple>
                    <v-chip filter class="chip" small v-for="i in 10" :key="i">
                      تعز
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
            </div>
            <v-divider class="mt-3"></v-divider>
            <div>
              <v-card-text class="pa-2 text"> ألوان </v-card-text>
              <v-row no-gutters class="justify-space-between">
                <v-col>
                  <v-chip-group column multiple>
                    <v-chip
                      v-for="PerColor in Colors"
                      :key="PerColor"
                      color=""
                      class="chip"
                      :class="PerColor.Colors"
                      small
                      filter
                      outlined
                    >
                      {{ PerColor.ColorText }}
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
            </div>
            <v-divider class="mt-3"></v-divider>
            <div>
              <v-card-text class="pa-2 text"> السعر </v-card-text>
              <v-card-actions class="">
                <v-text-field
                  type="number"
                  dense
                  hide-details=""
                  outlined
                  placeholder="من"
                ></v-text-field>
                <v-icon class="mx-2" color="primary"
                  >mdi-arrow-left-thin</v-icon
                >
                <v-text-field
                  type="number"
                  dense
                  hide-details=""
                  outlined
                  placeholder="الى"
                ></v-text-field>
              </v-card-actions>
            </div>
            <v-divider class="mt-3"></v-divider>
            <div>
              <v-card-text class="pa-2 text"> الفئات </v-card-text>
              <v-row no-gutters>
                <v-col class="" cols="12">
                  <v-chip-group column multiple>
                    <v-chip filter class="chip" small v-for="i in 10" :key="i">
                      تعز
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
            </div>
            <v-divider class="mt-3"></v-divider>
            <div>
              <v-card-text class="pa-2 text"> العلامة التجارية </v-card-text>
              <v-row no-gutters>
                <v-col class="" cols="12">
                  <v-chip-group column multiple>
                    <v-chip filter class="chip" small v-for="i in 10" :key="i">
                      تعز
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
            </div>
            <v-divider class="mt-3"></v-divider>
            <div class="mb-4">
              <v-card-text class="pa-2 text"> الحالة </v-card-text>
              <v-row no-gutters>
                <v-col class="" cols="12">
                  <v-chip-group column multiple>
                    <v-chip filter class="chip" small v-for="i in 3" :key="i">
                      تعز
                    </v-chip>
                  </v-chip-group>
                </v-col>
              </v-row>
            </div>
          </v-card>
          <v-sheet color="white" height="50px">
            <v-row
              align="center"
              justify="center"
              no-gutters
              style="height: 100%"
            >
              <v-btn
                width="90%"
                elevation="0"
                class="btn blue white--text"
                @click="filterdialog = false"
              >
                عرض
              </v-btn>
            </v-row>
          </v-sheet>
        </v-sheet>
      </v-navigation-drawer>
    </div>
    <!-- fillter big screen from 960px and up -->
    <div class="hidden-sm-and-down">
      <!-- <v-card-title class="text pa-2">
        <v-icon right color="primary" size="16">mdi-filter-outline</v-icon>
        تصفية البحث
      </v-card-title> -->
      <v-list dense class="pt-0 transparent">
        <!-- places -->
        <v-subheader class="title">المناطق</v-subheader>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item v-for="i in 5" :key="i">
            <v-list-item-content>
              <v-list-item-title class="text">تعز</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
        <!-- Color -->
        <v-subheader class="title">ألوان</v-subheader>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-row no-gutters>
            <v-col cols="" v-for="PerColor in Colors" :key="PerColor">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title class="text">
                    {{ PerColor.ColorText }}
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-col>
          </v-row>
        </v-list-item-group>
        <!-- Categories -->
        <v-subheader class="title">الفئات</v-subheader>
        <v-list-item-group v-model="selectedItem">
          <v-row no-gutters>
            <v-col v-for="i in 10" :key="i">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title class="text">
                    محمد أمين شمسان الحريبي
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-col>
          </v-row>
        </v-list-item-group>
        <!-- Price -->
        <v-subheader class="title">السعر</v-subheader>
        <v-list-item-group v-model="selectedItem">
          <v-row no-gutters align="center" class="">
            <v-col class="mx-1">
              <v-text-field
                type="number"
                dense
                hide-details=""
                outlined
                placeholder="من"
              ></v-text-field>
            </v-col>
            -
            <v-col class="mx-1">
              <v-text-field
                type="number"
                dense
                tile
                hide-details=""
                outlined
                placeholder="الى"
              ></v-text-field>
            </v-col>
            <v-col cols="12" class="pa-3">
              <v-btn
                block
                height="32"
                x-small
                elevation="0"
                color="primary"
                class="text"
              >
                <v-icon color="white"> mdi-menu-left </v-icon>
              </v-btn>
            </v-col>
          </v-row>
        </v-list-item-group>
        <!-- brands -->
        <v-subheader class="title"> العلامة التجارية </v-subheader>
        <v-list-item-group v-model="selectedItem">
          <v-row no-gutters>
            <v-col v-for="i in 10" :key="i">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title class="text">
                    محمد أمين شمسان الحريبي
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-col>
          </v-row>
        </v-list-item-group>
        <!-- condition  -->
        <v-subheader class="title"> الحالة</v-subheader>
        <v-list-item-group v-model="selectedItem">
          <v-row no-gutters>
            <v-col v-for="i in 3" :key="i">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title class="text"> الحريبي </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-col>
          </v-row>
        </v-list-item-group>
      </v-list>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilterSearch",
  components: {},
  data() {
    return {
      items: ["Foo", "Bar", "Fizz", "Buzz"],
      filterdialog: null,
      filter: false,
      drawer: false,
      price: null,
      condtion: null,
      location: null,
      admins: [
        ["Management", "mdi-account-multiple-outline"],
        ["Settings", "mdi-cog-outline"],
      ],
      cruds: [
        ["Create", "mdi-plus-outline"],
        ["Read", "mdi-file-outline"],
        ["Update", "mdi-update"],
        ["Delete", "mdi-delete"],
      ],
      Colors: [
        { ColorText: "أحمر", Colors: "red" },
        { ColorText: "برتقالي", Colors: "orange" },
        { ColorText: "أصفر", Colors: "yellow" },
        { ColorText: "أخضر", Colors: "green" },
        { ColorText: "أزرق", Colors: "blue" },
        { ColorText: "بنفسجي", Colors: "purple" },
        { ColorText: "زهري", Colors: "pink" },
        { ColorText: "بنى", Colors: "brown" },
        { ColorText: "رمادي", Colors: "grey" },
        { ColorText: "أسود", Colors: "black" },
        { ColorText: "أبيض", Colors: "white" },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.filtertion {
  background-color: #eee;
}
.filtertion-btn {
  letter-spacing: 0 !important;
  font-size: 13.5px !important;
  font-family: $fontfamliy3;
  font-weight: 600;
  color: $fontcolor !important;
}
.filtertion-list {
  letter-spacing: 0 !important;
  font-size: 14px !important;
  font-family: $fontfamliy3;
  font-weight: 600;
  color: #616161 !important;
}
.btn {
  letter-spacing: 0 !important;
  font-size: 18px;
  font-family: $fontfamliy3 !important;
  font-weight: 600 !important;
  @media (max-width: 600px) {
    font-size: 16px !important;
  }
}
::v-deep input {
  font-family: $fontfamliy3;
  font-size: 14px !important;
  letter-spacing: 0;
}

.text {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
  font-size: 14px !important;
  color: $fontcolorlinks;
  font-weight: 600;
}

::v-deep .v-subheader.title.theme--light.title {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 14px !important;
  color: $fontcolor;
  font-weight: 600;
}
.chip {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 14px !important;
}
::v-deep .theme--light.v-chip--active:before {
  opacity: 0 !important;
}
::v-deep .v-list--dense .v-list-item {
  min-height: 32px;
}
// }
// ::v-deep .v-chip.v-size--default {
//   height: 30px;
//   border-radius: 2px !important;
// }
/* Chrome, Safari, Edge, Opera */
::v-deep input::-webkit-outer-spin-button,
::v-deep input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
::v-deep .v-input__slot {
  min-height: 25px !important;
  justify-content: center;
}
::v-deep .v-avatar {
  @media (max-width: 600px) {
    height: 22px !important;
    min-width: 22px !important;
    width: 22px !important;
  }
}
::v-deep label.v-label.theme--light {
  font-family: $fontfamliy3;
  letter-spacing: 0 !important;
}
::v-deep .v-slide-group__content {
  justify-content: center;
}
::v-deep .v-navigation-drawer__content {
  z-index: 21 !important;
}
</style>
