<template>
  <div class="Services">
    <v-card-actions class="justify-center">
      <!-- Trusted  -->
      <v-btn
        @click="Trusted = true"
        v-bind:class="{
          IsTrue: Trusted,
        }"
      >
        <v-icon v-if="Trusted" right class="white--text"> mdi-check </v-icon>
        توثيق الأعلان
      </v-btn>
      <!-- feature  -->
      <v-btn
        :disabled="Upgrade"
        @click="feature = true"
        v-bind:class="{
          IsTrue: feature,
        }"
      >
        تعزيز الأعلان
      </v-btn>
      <!-- Upgrade  -->
      <v-btn
        :disabled="feature"
        @click="Upgrade = true"
        v-bind:class="{
          IsTrue: Upgrade,
        }"
      >
        <v-icon v-if="Upgrade" right class="white--text"> mdi-check </v-icon>
        ترقية الأعلان
      </v-btn>
    </v-card-actions>
    <v-card flat tile color="transparent">
      <v-card-subtitle v-if="Upgrade">
        تم الترقية المدة <span>60</span> يوماً
      </v-card-subtitle>
      <v-card-subtitle v-if="feature">
        تم التعزيز المدة <span>60</span> يوماً
      </v-card-subtitle>
      <v-card-subtitle v-if="pause"> تم توقيف الأعلان </v-card-subtitle>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "Services",
  data() {
    return {
      Upgrade: false,
      Trusted: false,
      feature: false,
      pause: false,
      delete: false,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Services {
  width: 100%;
  font-family: $fontfamliy;
  letter-spacing: 0px;
  a {
    font-family: $fontfamliy;
    letter-spacing: 0px;
    margin: 0 2px !important;
    border: 1px solid rgba(128, 128, 128, 0.477) !important;
    padding: 3px;
    border-radius: 5px !important;
    color: $color-6;
    font-size: 14px !important;
    font-weight: 500;
  }
  .IsTrue {
    background-color: #1976d2 !important;
    color: $fontcolorsm;
  }
  .IsPaused {
    background-color: #ef6c00 !important;
    color: $fontcolorsm;
  }
  .v-icon.v-icon {
    font-size: 20px;
  }
}
</style>
