<template>
  <div class="dashboard">
    <v-subheader
      class="py-0 d-flex justify-space-between rounded-lg grey--text"
    >
      <h2>Dashboard</h2>
      <v-spacer></v-spacer>
      <pop-up />
    </v-subheader>
    <br />
    <v-row class="mt-2">
      <v-col lg="7" cols="12">
        <v-row>
          <v-col
            lg="6"
            cols="12"
            v-for="(item, index) in activityLog"
            :key="index"
          >
            <v-card elevation="2" class="rounded-lg">
              <v-card-text class="d-flex justify-space-between align-center">
                <div>
                  <strong>{{ item.title }}</strong> <br />
                  <span>Last 3 weeks</span>
                </div>
                <v-icon :color="item.color" large>{{ item.icon }}</v-icon>
              </v-card-text>
              <v-divider class="mx-3 mt-4"></v-divider>
              <v-icon class="ma-3" small> mdi-clock </v-icon>
              <span class="text-caption grey--text font-weight-light"
                >last registration 26 minutes ago</span
              >
            </v-card>
          </v-col>
        </v-row>
        <v-card>
          <gradient-line-chart />
        </v-card>
      </v-col>
      <v-col lg="5" cols="12">
        <v-card class="mx-auto pb-3" max-width="460">
          <v-card dark flat>
            <v-img
              src="https://images.pexels.com/photos/140945/pexels-photo-140945.jpeg?auto=compress&cs=tinysrgb&w=600"
              gradient="to top, rgba(0,0,0,.44), rgba(0,0,0,.44)"
            >
              <v-container class="fill-height">
                <v-row align="center">
                  <v-row justify="center">
                    <div class="text-h5 font-weight-light">Activities</div>
                  </v-row>
                </v-row>
              </v-container>
            </v-img>
          </v-card>
          <v-card-text class="py-0">
            <v-timeline align-top dense>
              <v-timeline-item color="pink" small>
                <v-row class="pt-1">
                  <v-col cols="3">
                    <strong>5pm</strong>
                  </v-col>
                  <v-col>
                    <strong>New Icon</strong>
                    <div class="text-caption">Mobile App</div>
                  </v-col>
                </v-row>
              </v-timeline-item>

              <v-timeline-item color="teal lighten-3" small>
                <v-row class="pt-1">
                  <v-col cols="3">
                    <strong>3-4pm</strong>
                  </v-col>
                  <v-col>
                    <strong>Design Stand Up</strong>
                    <div class="text-caption mb-2">Hangouts</div>
                  </v-col>
                </v-row>
              </v-timeline-item>

              <v-timeline-item color="pink" small>
                <v-row class="pt-1">
                  <v-col cols="3">
                    <strong>12pm</strong>
                  </v-col>
                  <v-col>
                    <strong>Lunch break</strong>
                  </v-col>
                </v-row>
              </v-timeline-item>

              <v-timeline-item color="teal lighten-3" small>
                <v-row class="pt-1">
                  <v-col cols="3">
                    <strong>9-11am</strong>
                  </v-col>
                  <v-col>
                    <strong>Finish Home Screen</strong>
                    <div class="text-caption">Web App</div>
                  </v-col>
                </v-row>
              </v-timeline-item>
              <v-timeline-item color="teal" small>
                <v-row class="pt-1">
                  <v-col cols="3">
                    <strong>9-11am</strong>
                  </v-col>
                  <v-col>
                    <strong>Finish Home Screen</strong>
                    <div class="text-caption">Web App</div>
                  </v-col>
                </v-row>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row class="mt-2">
      <v-col lg="12">
        <v-card class="mr-4">
          <v-card-title>
            All Users
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
            :headers="headers"
            :items="desserts"
            :search="search"
          ></v-data-table>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import PopUp from "../components/PopUp.vue";
import GradientLineChart from "../components/GradientLineChart.vue";
import indexLayout from "../layouts/indexLayout.vue";
export default {
  components: { PopUp, GradientLineChart },
  created() {
    this.$emit("update:layout", indexLayout);
  },
  data() {
    return {
      activityLog: [
        {
          title: "Total Products",
          amount: 100,
          icon: "mdi-earth",
          color: "green accent-4",
        },
        {
          title: "Total Customer",
          amount: 200,
          icon: "mdi-account-group-outline",
          color: "lime darken-2",
        },
        {
          title: "Total Sale",
          amount: 300,
          icon: "mdi-shopping",
          color: "orange lighten-1",
        },
        {
          title: "Pending Orders",
          amount: 400,
          icon: "mdi-database-plus",
          color: "red accent-4",
        },
      ],
      search: "",
      headers: [
        {
          text: "Dessert (100g serving)",
          align: "start",
          filterable: false,
          value: "name",
        },
        { text: "Calories", value: "calories" },
        { text: "Fat (g)", value: "fat" },
        { text: "Carbs (g)", value: "carbs" },
        { text: "Protein (g)", value: "protein" },
        { text: "Iron (%)", value: "iron" },
      ],
      desserts: [
        {
          name: "Frozen Yogurt",
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: "1%",
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: "1%",
        },
        {
          name: "Eclair",
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: "7%",
        },
        {
          name: "Ice cream sandwich",
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: "1%",
        },
        {
          name: "Eclair",
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: "7%",
        },
      ],
    };
  },
};
</script>

<style scoped>
.overlap-icon {
  position: absolute;
  top: -33px;
  text-align: center;
  padding-top: 12px;
}
</style>