<template>
  <Header />
  <router-view />
</template>

<script>
import Header from "./components/Header.vue";

export default {
  components: {
    Header,
  },
};
</script>



<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Dosis, sans-serif;
}

#main {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 64.75px);
  background: hsla(18, 76%, 85%, 1);

  background: linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  background: -moz-linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  background: -webkit-linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  filter: progid: DXImageTransform.Microsoft.gradient( startColorstr="#F6CFBE", endColorstr="#B9DCF2", GradientType=1 );
}

.alert {
  color: red;
}

.login {
  text-decoration: none;
  color: black;
  font-size: 18px;
  margin-right: 0.6rem;
}

.logo {
  width: 80px;
  background: none;
}

.logo + p {
  font-size: 18px;
}

.all-content {
  background: hsla(18, 76%, 85%, 1);

  background: linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  background: -moz-linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  background: -webkit-linear-gradient(
    90deg,
    hsla(18, 76%, 85%, 1) 0%,
    hsla(203, 69%, 84%, 1) 100%
  );

  filter: progid: DXImageTransform.Microsoft.gradient( startColorstr="#F6CFBE", endColorstr="#B9DCF2", GradientType=1 );
}

header {
  background-color: #fff;
  /* background-color: rgba(136, 132, 132, 0.07); */
  width: 100%;
  box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.296);
  position: relative;
}

.container {
  padding: 20px;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>

