<template>
  <v-dialog v-model="dialog" max-width="600px">
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        color="primary"
        small
        text
        v-bind="attrs"
        v-on="on"
        outlined
        rounded
      >
        <v-icon>mdi-plus-circle-multiple-outline</v-icon>
        <span>Add User</span>
      </v-btn>
    </template>
    <v-card>
      <v-card-title>
        <span class="text-h5">Add A New Project</span>
      </v-card-title>
      <v-card-text>
        <v-form class="px-3" ref="form">
          <v-text-field
            label="Title"
            v-model="title"
            prepend-icon="mdi-folder"
            :rules="nameRules"
          ></v-text-field>
          <v-textarea
            label="information"
            v-model="content"
            rows="2"
            prepend-icon=" mdi-pencil"
          ></v-textarea>
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="auto"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="date"
                label="Date"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker v-model="date" no-title scrollable>
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="menu = false"> Cancel </v-btn>
              <v-btn text color="primary" @click="$refs.menu.save(date)">
                OK
              </v-btn>
            </v-date-picker>
          </v-menu>
          <v-btn color="blue darken-1" text @click.prevent="submit()">
            Save
          </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data: () => ({
    dialog: false,
    date: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
      .toISOString()
      .substr(0, 10),
    menu: false,
    modal: false,
    title: "",
    content: "",
    nameRules: [
      (v) => (v && v.length >= 4) || "Name must be more than 4 characters",
    ],
  }),
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        console.log(this.title, this.content, this.date);
        this.dialog = false;
        this.title = "";
        this.content = "";
        this.date = new Date(
          Date.now() - new Date().getTimezoneOffset() * 60000
        )
          .toISOString()
          .substr(0, 10);
      }
    },
  },
};
</script>







         