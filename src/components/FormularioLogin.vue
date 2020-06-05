<template>
  <div id="FormularioLogin">
    <div class="form-group">
      <label for="exampleInputEmail1">Correlo electrónico</label>
      <input type="email" v-model="email" class="form-control" />
    </div>
    <div class="form-group">
      <label for="exampleInputPassword1">Contraseña</label>
      <input type="password" v-model="password" class="form-control" />
    </div>

    <p v-show="!ok" class="text-danger">Este usuario no está registrado</p>
    <button @click="login" class="btn btn-primary">Log in</button>
  </div>
</template>

<script>
export default {
  name: "FormularioLogin",
  data() {
    return {
      email: "",
      password: "",
      ok: true
    };
  },
  methods: {
    login() {
      let perfiles = JSON.parse(localStorage.getItem("perfiles"));
      let check = perfiles.find(
        p => p.email === this.email && p.password === this.password
      );
      if (check) {
        localStorage.setItem('user',JSON.stringify(check))
        this.$router.push({ name: "Home" });
      } else {
        this.ok = false;
      }
    }
  }
};
</script>


<style  scoped>
#FormularioLogin {
  width: 40%;
  margin: auto;
  border: 1px solid;
  padding: 20px;
  border-radius: 15px;
}
</style>
