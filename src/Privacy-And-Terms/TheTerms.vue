<template>
  <div class="TheTerms">
    <NavBar />
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-card>
            <v-card-title> أحكام وشروط استخدام الاعلانات المبوبة </v-card-title>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import NavBar from "../NavBar/TheNavBar.vue";
export default {
  name: "TheTerms",
  components: { NavBar },
  data() {
    return {};
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.TheTerms {
  width: 100%;
  min-height: 100vh;
}
</style>
