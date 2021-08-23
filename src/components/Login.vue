<template>
  <div>
    <main id="main">
      <div class="container">
        <div class="main-content">
          <div class="first-section">
            <h2>Welcome To The VueApp</h2>
            <p>Enter your details in the left section</p>
          </div>
          <div class="second-section">
            <h1>Login</h1>
            <div class="icons">
              <fa
                class="icon"
                :icon="{ prefix: 'fab', iconName: 'facebook' }"
              />
              <fa class="icon" :icon="{ prefix: 'fab', iconName: 'google' }" />
            </div>
            <form @submit.prevent="nextPage">
              <div class="input-group">
                <label>Email</label>
                <input type="email" v-model="username" />
              </div>
              <div class="input-group">
                <label>Password</label>
                <div class="password-show">
                  <input :type="passwordText" v-model="password" />
                  <fa class="pass-change" :icon="show" @click="checkPassword" />
                </div>
                <span class="alert" v-if="isFieldEmpty"
                  >Field cannot be empty</span
                >
                <span class="alert" v-if="isUserDoesnotExist"
                  >User Does Not Exist</span
                >
              </div>
              <div class="login-info">
                <button class="button-login">Login</button>
                <a href="#" class="forgot-password">Forgot Password?</a>
              </div>
            </form>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      passwordText: "password",
      username: "",
      password: "",
      isFieldEmpty: false,
      isUserDoesnotExist: false,
      loginText: "Login",
      show: "eye",
      users: "",
    };
  },
  methods: {
    nextPage() {
      const userExists = this.users.some(
        (user) => user.email === this.username
      );
      if (this.username === "" || this.password === "") {
        this.isFieldEmpty = true;
      } else if (this.username !== "" && this.password !== "" && !userExists) {
        this.isUserDoesnotExist = true;
        this.isFieldEmpty = false;
      } else {
        this.isEmptyLogin = false;
        this.isEmptyPassword = false;
        this.$router.push({
          name: "Dashboard",
          params: { username: this.username },
        });
      }
    },
    checkPassword() {
      if (this.show === "eye") {
        this.show = "eye-slash";
        this.passwordText = "text";
      } else {
        this.show = "eye";
        this.passwordText = "password";
      }
    },
  },
  mounted() {
    if (localStorage.getItem("usersData")) {
      this.users = JSON.parse(localStorage.getItem("usersData"));
      console.log(this.users);
    }
  },
};
</script>


<style scoped>
#main .main-content {
  display: flex;
  box-shadow: 3px 3px 8px rgba(0, 0, 0, 0.405);
}

#main .main-content .first-section {
  display: flex;
  padding: 30px;
  display: flex;
  flex-direction: column;
  text-align: center;
  min-height: 300px;
  background-color: lightgreen;
  justify-content: center;
}

#main .main-content .first-section h2 {
  max-width: 200px;
  margin-bottom: 20px;
}

#main .main-content .second-section {
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #fff;
}

#main .main-content .second-section h1 {
  color: lightgreen;
  margin-bottom: 20px;
}

#main .main-content .second-section .icons {
  margin-bottom: 30px;
}

.icon {
  font-size: 33px;
  border: 1px solid black;
  border-radius: 50%;
  padding: 5px;
  margin-right: 10px;
  cursor: pointer;
}

.icon:hover {
  background-color: rgba(0, 0, 0, 0.07);
}

#main .main-content .second-section .icons p {
  margin-right: 10px;
}

#main .main-content .second-section p {
  margin-bottom: 20px;
}

#main .main-content .second-section .input-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
  width: 300px;
}

#main .main-content .second-section .input-group .password-show {
  display: flex;
  align-items: center;
}

#main .main-content .second-section .input-group .password-show .pass-change {
  cursor: pointer;
}

#main
  .main-content
  .second-section
  .input-group
  .password-show
  .pass-change:hover {
  color: rgba(0, 0, 0, 0.357);
}

#main .main-content .second-section .input-group label {
  margin-bottom: 5px;
}

#main .main-content .second-section .input-group input {
  border: 1px solid black;
  background: #fff;
  outline: none;
  padding: 10px;
  color: rgba(0, 0, 0, 0.529);
  width: 100%;
  border-radius: 5px;
  width: 260px;
  margin-right: 5px;
}

#main .main-content .second-section .input-group input:focus {
  border-color: lightgreen;
  border-width: 2px;
}

.login-info {
  display: flex;
  justify-content: space-between;
}

.button-login {
  border: none;
  background: lightgreen;
  padding: 10px 30px;
  border-radius: 30px;
  cursor: pointer;
  transition: 0.2s;
  font-weight: bold;
}

.button-login:hover {
  background-color: rgba(144, 238, 144, 0.679);
  padding-left: 35px;
}

.button-login:active {
  background-color: rgb(84, 163, 84);
}

.forgot-password {
  text-decoration: none;
  color: rgba(0, 0, 0, 0.857);
}

.forgot-password:hover {
  color: rgba(0, 0, 0, 0.631);
}

@media (min-width: 300px) {
  #main .main-content .first-section {
    display: none;
  }
}

@media (min-width: 768px) {
  #main .main-content .first-section {
    display: flex;
  }
}

/* @media (min-width: 992px) {
}

@media (min-width: 1200px) {
}

@media (min-width: 1400px) {
} */
</style>
