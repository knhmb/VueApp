<template>
  <div>
    <!-- <Header :isTrue="$route.params.isTrue" /> -->
    <main id="main">
      <div class="container">
        <div class="main-content">
          <div class="first-section">
            <h2>Welcome To The VueApp</h2>
            <p>Enter your details in the left section</p>
          </div>
          <div class="second-section">
            <h1>Register</h1>
            <div class="icons">
              <fa
                class="icon"
                :icon="{ prefix: 'fab', iconName: 'facebook' }"
              />
              <fa class="icon" :icon="{ prefix: 'fab', iconName: 'google' }" />
            </div>
            <form @submit.prevent="registered">
              <div class="input-group">
                <label>Username</label>
                <input type="text" v-model="user.username" />
              </div>
              <div class="input-group">
                <label>Email</label>
                <input type="email" v-model="user.email" />
              </div>
              <div class="input-group">
                <label>Password</label>
                <div class="password-show">
                  <input v-model="user.password" type="password" />
                </div>
                <span v-if="isPasswordEmpty" class="alert"
                  >All Fields Must Be Filled</span
                >
                <span v-if="isUserRegistered" class="alert"
                  >Email Already Exists</span
                >
              </div>
              <div class="login-info">
                <button class="button-login">Resgister</button>
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
      isPasswordEmpty: false,
      isUserRegistered: false,
      user: {
        username: "",
        email: "",
        password: "",
      },
      users: [],
    };
  },
  methods: {
    registered() {
      const UserExists = this.users.some(
        (user) => user.email === this.user.email
      );
      if (
        this.user.password === "" ||
        this.user.email === "" ||
        this.user.username === ""
      ) {
        this.isPasswordEmpty = true;
      } else if (UserExists) {
        this.isUserRegistered = true;
      } else {
        this.isPasswordEmpty = false;
        this.users.unshift({
          username: this.user.username,
          email: this.user.email,
          password: this.user.password,
        });
        localStorage.setItem("usersData", JSON.stringify(this.users));
        this.$router.push({ name: "Login" });
      }
    },
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
  min-width: 260px;
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
  width: 100%;
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
</style>
