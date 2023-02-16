<template>
  <div class="CarReport">
    <v-container>
      <v-row>
        <v-col cols="12">
          <a
            @click="ShowCarReport = !ShowCarReport"
            class="justify-center black--text pa-0 py-2"
          >
            <v-icon v-text="ShowCarReport == true ? Up : down"></v-icon>
            عدد البلاغات
            <span class="mx-1">( 1 )</span>
          </a>
        </v-col>
      </v-row>
      <v-card v-if="ShowCarReport" class="pa-2 my-1">
        <v-card-text class="red--text pa-0 my-1">
          نوع البلاغ :
          <span class="black--text">إعلان متكرر</span>
        </v-card-text>
        <v-card-text class="red--text pa-0 my-1">
          أسم صاحب البلاغ :
          <span class="black--text">إعلان متكرر</span>
        </v-card-text>
        <v-card-text class="red--text pa-0 my-1">
          هاتف صاحب البلاغ :
          <span class="black--text">إعلان متكرر</span>
        </v-card-text>
        <v-card-text class="red--text pa-0 my-1">
          تعليق صاحب البلاغ :
          <span class="black--text">
            إعلان متكررإعلان متكررإعلان متكررإعلان متكررإعلان متكررإعلان
            متكررإعلان متكررإعلان متكرر
          </span>
        </v-card-text>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "CarReport",
  data() {
    return {
      ShowCarReport: false,
      Up: "mdi-chevron-up",
      down: "mdi-chevron-down",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";

.CarReport {
  width: 100%;
  font-family: $fontfamliy !important;
  letter-spacing: 0px;
}
</style>
