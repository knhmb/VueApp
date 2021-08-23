<template>
  <header id="head">
    <div class="container">
      <div class="header-content">
        <img
          class="logo"
          src="https://cdn.vuetifyjs.com/docs/images/logos/vuetify-logo-light-text.svg"
          alt=""
        />
        <router-link to="/" class="login">VueApp</router-link>
        <router-link
          @click="removeData"
          v-if="$route.path === '/dashboard'"
          to="/"
          class="login"
          >Logout</router-link
        >
        <div v-else>
          <router-link to="/login" class="login">Login</router-link>
          <router-link to="/register" class="login">Register</router-link>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  props: {
    isTrue: {
      type: Boolean,
    },
  },
  methods: {
    removeData() {
      if (localStorage.getItem("usersData")) {
        localStorage.removeItem("usersData");
      }
    },
  },
  created() {
    console.log(this.$route);
  },
};
</script>
