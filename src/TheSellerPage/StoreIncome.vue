<template>
  <div class="PasswordChange">
    <v-container class="container">
      <v-toolbar tile flat>
        <v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          :return-value.sync="date"
          transition="scale-transition"
          offset-x
          left
          max-width="290px"
          min-width="auto"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-card-title v-bind="attrs" v-on="on" class="pa-0 title">
              <v-chip class="title" color="light-blue" label text-color="white">
                التاريخ :
                <span class="mx-1" v-text="date"></span>
              </v-chip>
            </v-card-title>
          </template>
          <v-date-picker v-model="date" type="month" no-title scrollable>
            <v-spacer></v-spacer>
            <v-btn text color="primary" @click="menu = false"> Cancel </v-btn>
            <v-btn text color="primary" @click="$refs.menu.save(date)">
              OK
            </v-btn>
          </v-date-picker>
        </v-menu>
        <v-spacer></v-spacer>
        <v-btn
          small
          class="print-text"
          color="blue-grey lighten-4"
          elevation="0"
        >
          طباعة
          <v-icon right> mdi-printer-outline </v-icon>
        </v-btn>
      </v-toolbar>
      <div>
        <v-data-table
          :headers="headers"
          :items="desserts"
          :page.sync="page"
          :items-per-page="itemsPerPage"
          hide-default-footer
          class="elevation-1 rounded-0"
          @page-count="pageCount = $event"
        >
          <template v-slot:item.TotalPrice="{ item }">
            <v-chip label small color="light-blue lighten-2" dark>
              {{ item.TotalPrice }}
            </v-chip>
          </template>
          <template v-slot:item.ratio="{ item }">
            <v-chip label small color="orange lighten-2" dark>
              {{ item.ratio }}
            </v-chip>
          </template>
          <template v-slot:item.CustomerNetProfit="{ item }">
            <v-chip label small color="green accent-4" dark>
              {{ item.CustomerNetProfit }}
            </v-chip>
          </template>
        </v-data-table>
        <div v-if="itemsPerPage > 10" class="text-center pt-2">
          <v-pagination
            class="elevation-0"
            circle
            v-model="page"
            :length="pageCount"
          ></v-pagination>
        </div>
      </div>
    </v-container>
  </div>
</template>
<script>
export default {
  name: "PasswordChange",
  data() {
    return {
      date: new Date().toISOString().substr(0, 7),
      menu: false,
      modal: false,
      page: 1,
      pageCount: 0,
      itemsPerPage: 10,
      headers: [
        {
          text: "رقم المنتج",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "الوقت", value: "date" },
        { text: "العدد", value: "quantity" },
        { text: "السعر الأجمالي", value: "TotalPrice" },
        { text: "نسبة الموقع", value: "ratio" },
        { text: "صافي ربح العميل", value: "CustomerNetProfit" },
      ],
      desserts: [
        {
          name: "0122112442",
          date: "05.25 ص ب",
          quantity: 3,
          TotalPrice: 24,
          ratio: 4.0,
          CustomerNetProfit: "1%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 1,
          TotalPrice: 37,
          ratio: 4.3,
          CustomerNetProfit: "1%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 1,
          TotalPrice: 23,
          ratio: 6.0,
          CustomerNetProfit: "7%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 2,
          TotalPrice: 67,
          ratio: 4.3,
          CustomerNetProfit: "8%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 2,
          TotalPrice: 49,
          ratio: 3.9,
          CustomerNetProfit: "16%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 1,
          TotalPrice: 94,
          ratio: 0.0,
          CustomerNetProfit: "0%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 1,
          TotalPrice: 98,
          ratio: 0,
          CustomerNetProfit: "2%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 2,
          TotalPrice: 87,
          ratio: 6.5,
          CustomerNetProfit: "45%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 1,
          TotalPrice: 51,
          ratio: 4.9,
          CustomerNetProfit: "22%",
        },
        {
          name: "0122112442",
          date: "15/8/2022",
          quantity: 2,
          TotalPrice: 65,
          ratio: 7,
          CustomerNetProfit: "6%",
        },
      ],
    };
  },
  methods: {
    getColor(calories) {
      if (calories > 400) return "red";
      else if (calories > 200) return "orange";
      else return "green";
    },
  },
};
</script>
<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.PasswordChange {
  width: 100%;
  min-height: 100vh;
  // @include flexcenter;
  @media (max-width: 600px) {
    margin-bottom: 50px;
  }
  .title {
    font-family: $fontfamliy3 !important;
    letter-spacing: 0 !important;
    font-size: 17px !important;
  }
  .line-span {
    width: 100%;
    height: 0.5px;
    background-color: rgb(231, 231, 231);
    display: block;
  }
  .container {
    @media (min-width: 960px) {
      max-width: 1212px !important;
    }
    @media (max-width: 450px) {
      padding: 5px !important;
    }
  }
}
::v-deep th.text-start {
  font-family: $fontfamliy3 !important;
  letter-spacing: 0 !important;
  font-size: 14px !important;
}
::v-deep td.text-start {
  font-family: $fontfamliy3 !important;
  // letter-spacing: 0 !important;
  font-size: 15px !important;
}
::v-deep span.v-chip.theme--dark.v-size--small {
  font-family: $fontfamliy3 !important;
  // letter-spacing: 0 !important;
  font-size: 15px !important;
  width: 60px;
  justify-content: center;
}
::v-deep .v-data-table__mobile-row__header {
  font-family: $fontfamliy3 !important;
  // letter-spacing: 0 !important;
  font-size: 13px !important;
  justify-content: center;
  color: $fontcolorlinks;
}
.print-text {
  font-family: $fontfamliy3 !important;
  font-size: 13px !important;
  letter-spacing: 0 !important;
  font-weight: 600;
}
</style>
