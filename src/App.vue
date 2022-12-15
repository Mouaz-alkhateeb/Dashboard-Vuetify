<template>
  <v-app id="inspire">
    <bar-app />
    <v-main class="grey lighten-4">
      <v-container class="py-8 px-6" fluid>
        <router-view></router-view> </v-container
      ><footer-app />
    </v-main>
  </v-app>
</template>

<script>
import BarApp from "./components/BarApp.vue";
import FooterApp from "./components/FooterApp.vue";

export default {
  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: false,
  }),
  components: { BarApp, FooterApp },
};
</script>
