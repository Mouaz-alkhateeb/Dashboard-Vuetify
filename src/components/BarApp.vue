<template>
  <nav>
    <v-app-bar app elevate-on-scroll fixed>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="font-weight-bold">Project Title</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-spacer></v-spacer>
      <v-btn text fab @click.prevent="coolor()">
        <v-icon>mdi-weather-night</v-icon>
      </v-btn>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <span
            v-bind="attrs"
            v-on="on"
            class="mx-5 mr-5"
            style="cursor: pointer"
          >
            <v-badge color="red" offset-x="10" offset-y="10" content="5">
              <v-icon>mdi-bell</v-icon></v-badge
            >
          </span>
        </template>
        <v-list three-line width="300">
          <template v-for="(item, index) in items">
            <v-subheader
              v-if="item.header"
              :key="item.header"
              v-text="item.header"
            ></v-subheader>

            <v-divider
              v-else-if="item.divider"
              :key="index"
              :inset="item.inset"
            ></v-divider>

            <v-list-item v-else :key="item.title">
              <v-list-item-avatar>
                <v-img :src="item.avatar"></v-img>
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title v-html="item.title"></v-list-item-title>
                <v-list-item-subtitle
                  v-html="item.subtitle"
                ></v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </template>
        </v-list>
      </v-menu>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <span
            v-bind="attrs"
            v-on="on"
            class="mx-5 mr-5"
            style="cursor: pointer"
          >
            <v-badge dot top left color="green" offset-x="10" offset-y="10">
              <v-avatar size="45">
                <img src="https://cdn.vuetifyjs.com/images/john.jpg"
              /></v-avatar>
            </v-badge>
          </span>
        </template>
        <v-list width="250" class="py-0" rounded>
          <v-list-item two-line>
            <v-list-item-avatar>
              <img src="https://randomuser.me/api/portraits/women/81.jpg" />
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title>Jane Smith</v-list-item-title>
              <v-list-item-subtitle>Logged In</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-divider />

          <v-list-item-group color="primary" class="mt-1 mb-1"
            ><v-list-item link v-for="(menu, i) in menus" :key="i">
              <v-list-item-icon>
                <v-icon>{{ menu.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-title>
                {{ menu.title }}
              </v-list-item-title>
            </v-list-item></v-list-item-group
          >
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-navigation-drawer app v-model="drawer" dark>
      <v-img
        height="160"
        class="pa-4"
        src="https://images.unsplash.com/photo-1532210317995-cc56d90177d9?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=Mnw0NTMzNXwwfDF8c2VhcmNofDE5fHxiYWNrZ3JvdW5kfGVufDB8fHx8MTY3MDg3MDI4MQ&ixlib=rb-4.0.3&q=80&w=200"
      >
        <div class="text-center">
          <v-avatar class="ma-4" color="grey darken-1" size="80">
            <v-img src="https://cdn.vuetifyjs.com/images/john.jpg" />
          </v-avatar>
          <h2 class="white--text">Mouaz Alkhateeb</h2>
        </div>
      </v-img>

      <v-divider></v-divider>

      <v-list rounded>
        <v-list-item
          v-for="[icon, text, route] in links"
          :key="icon"
          link
          :to="route"
        >
          <v-list-item-icon>
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      drawer: true,
      links: [
        ["mdi-home", "Dashboard", "/"],
        ["mdi-account", "Profile", "profile"],
        ["mdi-clipboard-list-outline", "Products"],
        ["mdi-card-account-details-outline", "Orders"],
        ["mdi-login", "Login", "login"],
        ["mdi-cog", "System Setting"],
      ],
      menus: [
        { title: "Profile", icon: "mdi-account" },
        { title: "Change Password", icon: "mdi-key" },
        { title: "Setting", icon: "mdi-cog" },
        { title: "Logout", icon: "mdi-logout" },
      ],
      items: [
        {
          avatar: "https://cdn.vuetifyjs.com/images/lists/1.jpg",
          title: "Brunch this weekend?",
          subtitle: `<span class="text--primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
        },
        { divider: true, inset: true },
        {
          avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
          title: 'Summer BBQ <span class="grey--text text--lighten-1">4</span>',
          subtitle: `<span class="text--primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
        },
        { divider: true, inset: true },
        {
          avatar: "https://cdn.vuetifyjs.com/images/lists/3.jpg",
          title: "Oui oui",
          subtitle:
            '<span class="text--primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
        },
        { divider: true, inset: true },
        {
          avatar: "https://cdn.vuetifyjs.com/images/lists/4.jpg",
          title: "Birthday gift",
          subtitle:
            '<span class="text--primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
        },
        { divider: true, inset: true },
        {
          avatar: "https://cdn.vuetifyjs.com/images/lists/5.jpg",
          title: "Recipe to try",
          subtitle:
            '<span class="text--primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
        },
      ],
    };
  },
  methods: {
    coolor() {
      if (!this.$vuetify.theme.dark) {
        this.$vuetify.theme.dark = true;
      } else {
        this.$vuetify.theme.dark = false;
      }
    },
  },
};
</script>