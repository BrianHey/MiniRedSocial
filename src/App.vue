<template>
  <div id="app">
    <div id="nav">
      |
      <router-link to="/Login" v-show="!user">Login</router-link>|
      <router-link to="/" v-show="user">Home</router-link>|
      <router-link to="/Registro" v-show="!user">Registrarse</router-link>|
      <p @click="logout" v-show="user">Log out</p>
    </div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>


<script>
export default {
  data() {
    return {
      user: false
    };
  },
  mounted() {
    let check = JSON.parse(localStorage.getItem("user"));
    check ? (this.user = true) : (this.user = false);
  },
  updated() {
    let check = JSON.parse(localStorage.getItem("user"));
    check ? (this.user = true) : (this.user = false);

    // check ? false : this.$router.push({ name: "Login" });
  },
  methods: {
    logout() {
      localStorage.removeItem("user");
      this.$router.push({ name: "Login" });
    }
  }
};
</script>
