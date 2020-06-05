<template>
  <div class="about">
    <h1>Log in</h1>
    <FormularioLogin />
  </div>
</template>

<script>
import FormularioLogin from "../components/FormularioLogin";
export default {
  name: "Login",
  components: {
    FormularioLogin
  },
  beforeCreate() {
    let user = JSON.parse(localStorage.getItem('user'))
    user ? this.$router.push({name: 'Home'}) : false 
  }
};
</script>
