<template>
  <div id="FormularioRegistro">
    <div class="form-group">
      <label for="exampleInputEmail1">Foto de perfil</label>
      <div class="foto" :style="{ backgroundImage: 'url(' + datos.picture.large +')' }"></div>
    </div>
    <div class="form-group">
      <label for="exampleInputEmail1">Nombre</label>
      <input type="text" class="form-control" v-model="name" />
    </div>
    <div class="form-group">
      <label for="exampleInputEmail1">Correlo electrónico</label>
      <input type="email" class="form-control" v-model="datos.email" />
    </div>
    <div class="form-group">
      <label for="exampleInputPassword1">Contraseña</label>
      <input v-model="password" type="password" class="form-control" />
    </div>
    <button @click="registrar" class="btn btn-primary">Registrar</button>
  </div>
</template>

<script>
export default {
  props: ["datos"],
  data() {
    return {
      password: ""
    };
  },
  methods: {
    registrar() {
      let perfil = {
        imgSrc: this.datos.picture.large,
        email: this.datos.email,
        name: this.name,
        password: this.password
      };
      let perfiles = JSON.parse(localStorage.getItem("perfiles"));
      perfiles.push(perfil);
      localStorage.setItem("perfiles", JSON.stringify(perfiles));
      this.$router.push({name: 'Login'})
    }
  },
  mounted() {
    localStorage.getItem("perfiles") == null
      ? localStorage.setItem("perfiles", JSON.stringify([]))
      : false;
  },
  computed: {
    name() {
      return `${this.datos.name.first} ${this.datos.name.last}`;
    }
  }
};
</script>

<style  scoped>
#FormularioRegistro {
  width: 40%;
  margin: auto;
  border: 1px solid;
  padding: 20px;
  border-radius: 15px;
}

.foto {
  background-position: center;
  background-size: cover;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin: auto;
}
</style>
