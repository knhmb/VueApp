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
        <router-link v-if="$route.path === '/dashboard'" to="/" class="login"
          >Logout</router-link
        >
        <router-link v-else to="/login" class="login">Login</router-link>
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
  created() {
    console.log(this.$route);
  },
};
</script>
