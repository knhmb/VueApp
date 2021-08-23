<template>
  <div id="main">
    <div class="all-users-content">
      <h1>All Users</h1>
      <hr />
      <div class="data-users">
        <h3>{{ usersData.username }}</h3>
      </div>
      <!-- <hr /> -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      usersData: {},
    };
  },
  created() {
    if (localStorage.getItem("usersData")) {
      const data = JSON.parse(localStorage.getItem("usersData"));
      for (let d of data) {
        this.usersData = { ...d };
      }
    }
  },
};
</script>



<style scoped>
.all-users-content {
  background-color: #fff;
  border-radius: 10px;
  min-width: 500px;
  min-height: 200px;
  padding: 0.3rem;
  /* display: flex; */
}

.all-users-content h1 {
  text-align: center;
}

.data-users {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>