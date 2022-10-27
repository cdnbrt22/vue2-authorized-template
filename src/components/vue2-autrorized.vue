<template>
  <v-app>
    <v-main>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 lg6>
            <v-card elevation-10 pa-3 style="border-radius: 10px">
              <v-row>
                <v-col cols="4" style="background-color: red"> </v-col>
                <v-col cols="8" class="px-8">
                  <img src="" alt="" />
                  <h2 class="pl-2 my-6">{{ name }}</h2>

                  <form class="px-2">
                    <v-text-field
                      name="username"
                      label="Username"
                      type="text"
                      dense
                      required
                      v-model="user"
                      @input="onInput"
                      :rules="[rules.requiredId]"
                      :color="color"
                      :append-icon="icon"
                      :rounded="rounded"
                      :filled="fill"
                    />
                    <v-text-field
                      name="password"
                      label="Password"
                      dense
                      required
                      :v-model="user"
                      :color="color"
                      :type="hidePassword ? 'password' : 'text'"
                      :append-icon="
                        hidePassword ? 'mdi-eye-off' : 'mdi-eye-outline'
                      "
                      :rules="[rules.requiredPw]"
                      @click:append="hidePassword = !hidePassword"
                      :rounded="rounded"
                      :filled="fill"
                    />
                    <div class="d-flex justify-end">
                      <v-btn
                        class="white--text"
                        v-bind="$attrs"
                        v-on="$listeners"
                        :color="color"
                      >
                        Login
                      </v-btn>
                    </div>
                  </form>
                </v-col>
              </v-row>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: "Name APP",
    },
    color: {
      type: String,
      default: "primary",
    },
    value: {
      type: String,
      default: "",
    },
    icon: {
      type: String,
    },
    rounded: {
      type: Boolean,
      default: false,
    },
    fill: {
      type: Boolean,
      default: false,
    },
    login: {
      login: String,
    },
  },

  data() {
    return {
      user: this.value,
      hidePassword: true,
      rules: {
        requiredId: (value) => !!value || "Please enter a valid username.",
        requiredPw: (value) => !!value || "The password field is required.",
      },
    };
  },

  created() {
    console.log(this.$attrs);
    console.log(this.$props);
    console.log(this.$listeners);
  },

  methods: {
    onInput(newInputValue) {
      this.user = console.log(newInputValue);
      this.$emit("msgChange", newInputValue);
    },
  },
  watch: {
    value(newVal) {
      console.log(newVal);
      this.msgCopy = newVal;
    },
  },
};
</script>
