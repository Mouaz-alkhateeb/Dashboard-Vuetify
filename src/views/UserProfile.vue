<template>
  <v-row>
    <v-col cols="12" md="8">
      <v-card class="pa-2" flat>
        <v-form>
          <v-container>
            <v-row>
              <v-col cols="12" md="6">
                <v-text-field label="First Name" class="purple-input" />
              </v-col>

              <v-col cols="12" md="6">
                <v-text-field label="Last Name" class="purple-input" />
              </v-col>

              <v-col cols="12">
                <v-text-field label="Adress" class="purple-input" />
              </v-col>

              <v-col cols="12" md="4">
                <v-text-field label="City" class="purple-input" />
              </v-col>

              <v-col cols="12" md="4">
                <v-text-field label="Country" class="purple-input" />
              </v-col>

              <v-col cols="12" md="4">
                <v-text-field
                  class="purple-input"
                  label="Postal Code"
                  type="number"
                />
              </v-col>

              <v-col cols="12">
                <v-textarea
                  class="purple-input"
                  label="About Me"
                  value="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
                />
              </v-col>

              <v-col cols="12" class="text-right">
                <v-btn color="primary" outlined rounded class="mr-0">
                  Update
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </v-card>
    </v-col>
    <v-col cols="12" md="4">
      <v-card class="text-center" flat>
        <v-img height="250" src="../assets/bg-profile.jpg">
          <v-responsive class="pt-15">
            <v-avatar size="150" class="grey darken-2 mb-0">
              <img src="https://cdn.vuetifyjs.com/images/john.jpg" />
            </v-avatar> </v-responsive
        ></v-img>
        <v-card-text class="text-center">
          <h2 class="display-2 font-weight-light mb-3">Alec Thompson</h2>
          <p class="font-weight-light grey--text">
            Don't be scared of the truth because we need to restart the human
            foundation in truth And I love you like Kanye loves Kanye I love
            Rick Owens’ bed design but the back is...
          </p>
          <v-btn color="primary" rounded outlined class="mr-0"> Follow </v-btn>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import indexLayout from "../layouts/indexLayout.vue";
export default {
  created() {
    this.$emit("update:layout", indexLayout);
  },
};
</script>
