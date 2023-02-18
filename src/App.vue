<template>
  <v-app class="bind-class-padding">
    <!-- view all the pages -->
    <v-main style="min-height: 75vh !important">
      <router-view />
    </v-main>
    <!-- this button to scroll up  -->
    <v-btn
      ref="button"
      icon
      elevation="0"
      x-large
      class="btn-up"
      color="white"
      v-bind:class="{
        'btn-up': scrollPosition < 600,
        'is-hidden': scrollPosition > 600,
      }"
      @click="$vuetify.goTo(target, options)"
    >
      <v-icon class="btn-up-icon">mdi-arrow-collapse-up</v-icon>
    </v-btn>
    <ClientNotification class="hidden-sm-and-down" />
    <!-- this the footer page  -->
    <Footer />
  </v-app>
</template>

<script>
import Footer from "./footer/footer.vue";
import ClientNotification from "./Chat/ClientNotification.vue";
export default {
  name: "App",
  components: {
    Footer,
    ClientNotification,
  },
  data() {
    return {
      drawer: false,
      type: "number",
      number: 0,
      duration: 300,
      offset: 0,
      scrollPosition: null,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },
  methods: {
    updateScroll() {
      this.scrollPosition = window.scrollY;
    },
  },
  computed: {
    target() {
      const value = this[this.type];
      if (!isNaN(value)) return Number(value);
      else return value;
    },
    options() {
      return {
        duration: this.duration,
        offset: this.offset,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800;900&display=swap");
@import "./scss/virables";
#app {
  width: 100%;
  position: relative;
  overflow: hidden;
}
.bind-class-padding {
  @media (max-width: 600px) {
    // margin-bottom: 50px;
  }
}
.v-main {
  padding: 0px !important;
}
::v-deep .v-application--wrap {
  min-height: 94vh !important;
}
.btn-up {
  position: fixed;
  bottom: 70px;
  right: 8px;
  overflow: hidden;
  z-index: 1;
  transform: scale(0);
  background: rgba(255, 255, 255, 0.908);
  transition: all 0.2s 0s linear !important;
  // opacity: 0;
  pointer-events: none;
  @media (max-width: 600px) {
    bottom: 46px;
    transform: scale(0);
    z-index: 1;
  }
  .btn-up-icon {
    font-size: 22px !important;
    font-weight: 600;
    color: $color-2 !important;
  }
}
.is-hidden {
  // z-index: 18;
  pointer-events: auto;
  transform: scale(1);
  @media (max-width: 600px) {
    transform: scale(0.8);
  }
}
</style>
