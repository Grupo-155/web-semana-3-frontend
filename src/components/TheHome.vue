<template>
  <div>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid ">
        <form class="d-flex justify-content-between w-100">
          <a href="" class="navbar-brand">NavBar</a>
          <button
            class="btn btn-outline-secondary"
            type="submit"
            @click.prevent="logOutUser"
          >
            Log Out
          </button>
        </form>
      </div>
    </nav>
    <div class="card">
      <ul class="list-group list-group-flush w-100">
        <li class="list-group-item"><span>Nombre: </span>{{ user.nombre }}</li>
        <li class="list-group-item"><span>Email: </span> {{ user.email }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import vueJwtDecode from 'vue-jwt-decode';
export default {
  data() {
    return {
      user: {},
    };
  },
  methods: {
    logOutUser() {
      localStorage.removeItem("jwt");
      localStorage.removeItem("user");
      this.$router.push("/");
    },
    getUserData() {
      let token = localStorage.getItem("jwt");
       let user = localStorage.getItem("user");
      //let user = VueJwtDecode.decode(token);
      console.log(user);
      this.user = JSON.parse(user);
      //this.user = user;
    },
  },
  created() {
    this.getUserData();
  },
};
</script>

<style scoped></style>
