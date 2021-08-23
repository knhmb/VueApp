<template>
  <!-- <Header /> -->
  <div class="user-content all-content">
    <h1>User profile</h1>
    <div class="user-data">
      <h3>Update Information</h3>
      <div class="user-info">
        <label>Choose Avatar</label>
        <img src="" alt="" />
        <input type="file" @change="fileSelected" />
        <label>Change Username</label>
        <input type="text" :value="$route.params.username" />
        <label>Change Password</label>
        <input type="password" v-model="changedPassword" />
        <label>Confirm Password</label>
        <input type="password" v-model="confirmPassword" />
        <span v-if="isMatch" class="alert">Passwords do not match</span>
        <button @click="update">Update</button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      changedPassword: "",
      confirmPassword: "",
      isMatch: false,
      data: [],
    };
  },
  methods: {
    update() {
      if (this.changedPassword !== this.confirmPassword) {
        this.isMatch = true;
      } else {
        this.isMatch = false;
        alert("Information Updated");
      }
    },
  },
  mounted() {
    localStorage.getItem("usersData") &&
      this.data.push(JSON.parse(localStorage.getItem("usersData")));
    console.log(this.data);
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-content {
  /* background-color: #f1faee; */
  min-height: calc(100vh - 64.75px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.user-content > h1 {
  margin-bottom: 10px;
}

.user-content .user-data {
  background-color: #fff;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid lightgreen;
  min-height: 430px;
  border-radius: 20px;
  /* text-align: center; */
}

.user-content .user-data h3 {
  font-size: 25px;
  margin-bottom: 30px;
}

.user-content .user-data .user-info {
  display: flex;
  flex-direction: column;
}

.user-content .user-data .user-info input[type="file"] {
  margin-bottom: 20px;
}

.user-content .user-data .user-info label {
  margin-bottom: 5px;
}

.user-content .user-data .user-info input[type="text"],
input[type="password"] {
  border: 1px solid rgba(0, 0, 0, 0.398);
  background: #fff;
  outline: none;
  padding: 5px;
  color: rgba(0, 0, 0, 0.529);
  width: 100%;
  margin-bottom: 20px;
  border-radius: 5px;
}

.user-content .user-data .user-info input[type="text"]:focus,
input[type="password"]:focus {
  border-color: lightgreen;
  border-width: 2px;
}

.user-content .user-data .user-info button {
  background-color: lightgreen;
  padding: 7px;
  border: none;
  outline: none;
  border-radius: 10px;
  cursor: pointer;
}

.user-content .user-data .user-info button:hover {
  background-color: rgba(144, 238, 144, 0.686);
}

.user-content .user-data .user-info button:active {
  background: rgb(84, 163, 84);
}
</style>
