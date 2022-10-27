<template>
  <v-app>
    <Login
      color="red "
      v-model="user.username"
      name="Authorized"
      icon="mdi-account"
      :rounded="true"
      :fill="true"
      v-on:click="click"
    />

    <v-snackbar v-model="show" color="red" top>
      <div class="d-flex justify-center">{{ isResult }}</div>
    </v-snackbar>
  </v-app>
</template>

<script>
import Login from "@/components/vue2-autrorized.vue";

export default {
  name: "App",

  components: {
    Login,
  },

  data: () => ({
    user: {
      username: null,
      password: null,
    },
    show: false,
    isResult: "",
  }),

  mounted() {
    this.show;
  },

  methods: {
    click() {
      this.isResult = "Login Success";
      this.show = true;
      console.log("login success !!");
    },
  },
};
</script>
