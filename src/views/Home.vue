<template>
  <div class="home">
    <div class="row">
      <div class="col-3">
        <Newcomment @newcoment="newcoment" />
      </div>
      <div class="col-9">
        <Comentarios :comentarios="comentarios" />
      </div>
    </div>
  </div>
</template>

<script>
import Newcomment from "../components/Newcomment";
import Comentarios from "../components/Comentarios";
export default {
  name: "Home",
  components: {
    Newcomment,
    Comentarios
  },
  data() {
    return {
      comentarios: [],
      user: {}
    };
  },
  beforeCreate() {
    let user = JSON.parse(localStorage.getItem("user"));
    user ? false : this.$router.push({ name: "Registro" });
  },
  methods: {
    newcoment(newcoment) {
      this.comentarios.push({
        email: this.user.email,
        name: this.user.name,
        message: newcoment,
        imgSrc: this.user.imgSrc
      });
      localStorage.setItem("comentarios", JSON.stringify(this.comentarios));
    }
  },
  beforeMount() {
    let user = JSON.parse(localStorage.getItem("user"));
    this.user = user;
    let comentariosLS = localStorage.getItem("comentarios")
    comentariosLS == null
      ? localStorage.setItem("comentarios", JSON.stringify([]))
      : this.comentarios = JSON.parse(comentariosLS) ;
  }
};
</script>
