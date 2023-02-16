<template>
  <div class="Report">
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-card-title class="card-title"> البلاغات </v-card-title>
          <v-simple-table>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="header">نوع البلاغ</th>
                  <th class="header">رقم إعلان السيارة</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in desserts" :key="item.name">
                  <td>{{ item.name }}</td>
                  <td>{{ item.calories }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Report",
  data() {
    return {
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
        },
        {
          name: "Eclair",
          calories: 262,
        },
        {
          name: "Cupcake",
          calories: 305,
        },
        {
          name: "Gingerbread",
          calories: 356,
        },
        {
          name: "Jelly bean",
          calories: 375,
        },
        {
          name: "Lollipop",
          calories: 392,
        },
        {
          name: "Honeycomb",
          calories: 408,
        },
        {
          name: "Donut",
          calories: 452,
        },
        {
          name: "KitKat",
          calories: 518,
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/virables";
@import "@/scss/mixin";
.Report {
  width: 100%;
  min-height: 100vh;
  background-color: $color-background;
  padding: $padding;
  .card-title {
    font-family: $fontfamliy !important;
    letter-spacing: 0px;
    color: $color-6 !important;
  }
  .header {
    font-family: $fontfamliy !important;
    letter-spacing: 0px;
    font-size: 16px;
    font-weight: 500;
  }
}
</style>
