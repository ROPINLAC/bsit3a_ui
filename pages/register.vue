<template>
  <div>
    <div class="d-flex justify-center align-center" style="height: 100vh">
      <v-card width="400" class="elevation-6" style="background-color:rgba(225,0,0,0);">
        <div align="center">
          <v-img
            src="logoCompany.png"
            width="250"
          >
          </v-img>
        </div>

        <div class="mx-6 text-center">
          <v-card-text>
            <v-row>
              <v-col cols="12" md="6">
                <v-btn block outlined>
                  <v-icon color="red"> mdi-google </v-icon>

                  Google
                </v-btn>
              </v-col>

              <v-col cols="12" md="6">
                <v-btn block outlined>
                  <v-icon color="primary"> mdi-facebook </v-icon>

                  Facebook
                </v-btn>
              </v-col>
            </v-row>
          </v-card-text>

          <v-card-text>
            <v-row align="center">
              <v-divider class="mx-3" />

              <h5>OR</h5>

              <v-divider class="mx-3" />
            </v-row>
          </v-card-text>

          <v-card-text>
            <v-form ref="form" v-model="valid" lazy-validation>
              <v-text-field
                outlined
                label="E-mail"
                prepend-inner-icon="mdi-email"
                v-model="email"
                :rules="emailRules"
                required
              >
              </v-text-field>

              <v-text-field
                outlined
                type="Password"
                label="Password"
                prepend-inner-icon="mdi-lock"
                append-icon="mdi-eye-off"
                :rules="passRules"
                required
              >
              </v-text-field>

              <v-text-field
                outlined
                type="Password"
                label="Confirm Password"
                prepend-inner-icon="mdi-lock"
                append-icon="mdi-eye-off"
                :rules="cpassRules"
                required
              >
              </v-text-field>

              <v-btn block color="primary" @click="validate" :disabled="!valid">
                Sign Up
              </v-btn>

              <v-card-text>
                <a href="/" style="text-decoration: none"
                  >Already have an Account</a
                >
              </v-card-text>
            </v-form>
          </v-card-text>
        </div>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data: () => ({
    valid: true,
    password: "",
    passRules: [(v) => !!v || "Password is required"],
    cPassword: "",
    cpassRules: [(v) => !!v || "Confirm Password is required"],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
  }),

  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        console.log("Successfully Sign Up");
        this.$router.push("/");
      }
    },
  },
};
</script>