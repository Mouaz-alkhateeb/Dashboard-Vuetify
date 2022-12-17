<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="10">
        <v-card class="elevation-6 mt-10">
          <v-window v-model="step">
            <v-window-item :value="1">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-text class="mt-12">
                    <h4 class="text-center">Login into application</h4>
                    <h6 class="text-center grey--text">
                      Login into application
                    </h6>
                    <br />
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                        <v-text-field
                          dense
                          color="teal"
                          label="E-mail"
                          autocomplete="false"
                          class="mt-16"
                          v-model="email"
                          :rules="[rules.required, rules.email]"
                        ></v-text-field>
                        <v-text-field
                          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                          @click:append="show1 = !show1"
                          :type="show1 ? 'text' : 'password'"
                          v-model="password"
                          :rules="[rules.required, rules.min]"
                          hint="At least 8 characters"
                          dense
                          color="teal"
                          label="Password"
                          autocomplete="false"
                          class="mt-16"
                        ></v-text-field>
                        <v-row>
                          <v-col cols="12" sm="7">
                            <v-checkbox
                              label="Remember Me"
                              class="mt-n1"
                              color="teal"
                            >
                            </v-checkbox>
                          </v-col>
                          <v-col cols="12" sm="5">
                            <span class="caption teal--text"
                              >Forget Password</span
                            >
                          </v-col>
                        </v-row>
                        <v-btn color="teal" dark block rounded> Login </v-btn>
                        <h5 class="text-center grey--text mt-4 mb-3">
                          Or Login By Social media
                        </h5>
                        <div
                          class="
                            d-flex
                            justify-space-between
                            align-center
                            mx-10
                            mb-16
                          "
                        >
                          <v-btn color="white" text fab>
                            <v-icon large color="blue">mdi-facebook</v-icon>
                          </v-btn>
                          <v-btn color="white" text fab>
                            <v-icon large color="red">mdi-google</v-icon>
                          </v-btn>
                          <v-btn color="white" text fab>
                            <v-icon large color="light-blue lighten-3"
                              >mdi-twitter</v-icon
                            >
                          </v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-col>
                <v-col cols="12" md="6" class="teal rounded-bl-xl">
                  <div style="text-align: center; padding: 180px 0">
                    <v-card-text class="white--text">
                      <h3 class="text-center">Don't Have an Account Yet?</h3>
                      <h6 class="text-center">
                        Let's get you all set up so you can start creating your
                        your first<br />
                        onboarding experience
                      </h6>
                    </v-card-text>
                    <div class="text-center">
                      <v-btn outlined dark rounded @click="step++"
                        >SIGN UP</v-btn
                      >
                    </div>
                  </div>
                </v-col>
              </v-row>
            </v-window-item>
            <v-window-item :value="2">
              <v-row>
                <v-col cols="12" md="6" class="teal rounded-br-xl">
                  <div style="text-align: center; padding: 180px 0">
                    <v-card-text class="white--text">
                      <h3 class="text-center">Alredy Signed up?</h3>
                      <h6 class="text-center">
                        Log in to your account so you can continue building
                        and<br />
                        editing your onboarding flows
                      </h6>
                    </v-card-text>
                    <div class="text-center">
                      <v-btn rounded outlined dark @click="step--"
                        >Log in</v-btn
                      >
                    </div>
                  </div>
                </v-col>
                <v-col cols="12" md="6">
                  <v-card-text class="mt-12"
                    ><h4 class="text-center">Sign Up for an Account</h4>
                    <h6 class="text-center grey--text">
                      Let's get you all set up so you can start creatin your
                      <br />
                      first onboarding experiance
                    </h6>
                    <v-row align="center" justify="center">
                      <v-col cols="12" sm="8">
                        <v-row
                          ><v-col cols="12" sm="6">
                            <v-text-field
                              label="First Name"
                              dense
                              color="teal"
                              autocomplete="false"
                            ></v-text-field>
                          </v-col>
                          <v-col cols="12" sm="6">
                            <v-text-field
                              label="Last Name"
                              dense
                              color="teal"
                              autocomplete="false"
                            ></v-text-field>
                          </v-col>
                        </v-row>
                        <v-text-field
                          dense
                          color="teal"
                          label="E-mail"
                          autocomplete="false"
                          class="mt-12"
                          v-model="email"
                          :rules="[rules.required, rules.email]"
                        ></v-text-field>
                        <v-text-field
                          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                          @click:append="show1 = !show1"
                          :type="show1 ? 'text' : 'password'"
                          v-model="password"
                          :rules="[rules.required, rules.min]"
                          hint="At least 8 characters"
                          dense
                          color="teal"
                          label="Password"
                          autocomplete="false"
                          class="mt-12"
                        ></v-text-field>

                        <v-row>
                          <v-col cols="12" sm="7"
                            ><v-checkbox
                              label="I Accept"
                              class="mt-n1"
                              color="teal"
                            >
                            </v-checkbox
                          ></v-col>
                          <v-col cols="12" sm="5">
                            <span class="caption teal--text ml-n4"
                              >Terms &Conditions</span
                            >
                          </v-col>
                        </v-row>
                        <v-btn color="teal" dark block rounded>Sign up</v-btn>
                        <h5 class="text-center grey--text mt-4 mb-3">
                          Or Sign up using
                        </h5>
                        <div
                          class="
                            d-flex
                            justify-space-between
                            align-center
                            mx-10
                            mb-11
                          "
                        >
                          <v-btn color="white" text fab>
                            <v-icon large color="blue">mdi-facebook</v-icon>
                          </v-btn>
                          <v-btn color="white" text fab>
                            <v-icon large color="red">mdi-google</v-icon>
                          </v-btn>
                          <v-btn color="white" text fab>
                            <v-icon large color="light-blue lighten-3"
                              >mdi-twitter</v-icon
                            >
                          </v-btn>
                        </div>
                      </v-col>
                    </v-row>
                  </v-card-text>
                </v-col>
              </v-row>
            </v-window-item>
          </v-window>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import LoginLayout from "../layouts/LoginLayout.vue";
export default {
  created() {
    this.$emit("update:layout", LoginLayout);
  },
  data() {
    return {
      show1: false,
      show2: true,
      password: "",
      rules: {
        required: (value) => !!value || "Required.",
        min: (v) => v.length >= 8 || "Min 8 characters",
        counter: (value) => value.length <= 20 || "Max 20 characters",
        email: (value) => {
          const pattern =
            /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
          return pattern.test(value) || "Invalid e-mail.";
        },
      },
      step: 1,
    };
  },
  props: {
    source: String,
  },
};
</script>
<style scoped>
.v-application .rounded-bl-xl {
  border-bottom-left-radius: 300px !important;
}

.v-application .rounded-br-xl {
  border-bottom-right-radius: 300px !important ;
}
</style>
