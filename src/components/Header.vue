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
        <div
          v-if="$route.path === '/dashboard' || $route.path === '/all-users'"
        >
          <router-link @click="removeData" to="/" class="login"
            >Logout</router-link
          >
          <router-link to="/all-users" class="login"
            >View All Users</router-link
          >
        </div>

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
  data() {
    return {
      isLocalStorage: false,
    };
  },
  methods: {
    removeData() {
      if (localStorage.getItem("usersData")) {
        localStorage.removeItem("usersData");
        this.isLocalStorage = false;
      }
    },
  },
  created() {
    console.log(this.$route);
  },
  mounted() {
    if (localStorage.getItem("usersData")) {
      this.isLocalStorage = true;
    }
  },
};
</script>
