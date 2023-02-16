<template>
  <div class="ThePrivacy">
    <NavBar />
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-card>
            <v-card-title> سياسة خصوصية شراء عملاء سيارة </v-card-title>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import NavBar from "../NavBar/TheNavBar.vue";
export default {
  name: "ThePrivacy",
  components: { NavBar },
  data() {
    return {};
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.ThePrivacy {
  width: 100%;
  min-height: 100vh;
}
</style>
