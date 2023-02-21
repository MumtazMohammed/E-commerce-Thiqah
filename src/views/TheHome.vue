<template>
  <v-main class="main">
    <NavBar />
    <OutAdvertisement />
    <Services />
    <TheCategorieSmallScreen />
    <BestOffer />
    <DailyOffer />
    <TopSale />
    <CompaniesCardAdv />
    <YouMightLikeIt />
    <FixedBottomNav class="hidden-md-and-up" />
    <Footer />
  </v-main>
</template>

<script>
import FixedBottomNav from "../NavBar/FixedBottomNav.vue";
import NavBar from "@/NavBar/TheNavBar.vue";
import TheCategorieSmallScreen from "../A-Home/TheCategorieSmallScreen.vue";
import OutAdvertisement from "@/Advertisement/OutAdvertisement.vue";
import BestOffer from "../A-Home/BestOffer.vue";
import DailyOffer from "../A-Home/DailyOffer.vue";
import TopSale from "../A-Home/TopSale.vue";
import Services from "../A-Home/Services.vue";
import CompaniesCardAdv from "../A-Home/CompaniesCardAdv.vue";
import YouMightLikeIt from "../A-Home/YouMightLikeIt.vue";
// import CarPartsCategories from "../A-Home/CarPartsCategories.vue";
import DateCar from "../data-json/car-data.json";
import AllDateCar from "../data-json/All-Car.json";
import CarType from "../data-json/CarType.json";
import Footer from "../footer/footer.vue";

const components = {
  OutAdvertisement,
  Services,
  CompaniesCardAdv,
  TheCategorieSmallScreen,
  BestOffer,
  DailyOffer,
  TopSale,
  YouMightLikeIt,
  NavBar,
  FixedBottomNav,
  Footer,
};
export default {
  name: "Home",
  components,
  data() {
    return {
      caritems: DateCar,
      AllDateCar,
      CarType: CarType,
    };
  },
};
</script>
<style lang="scss" scoped>
// .main {

// }
</style>
