<template>
  <div class="about">
    <h1>Registrar</h1>
    <FormularioRegistro  :datos="datos" />
  </div>
</template>

<script>
import FormularioRegistro from "../components/FormularioRegistro";
export default {
  name: "Registro",
  components: {
    FormularioRegistro
  },
  data() {
    return {
      datos: {
        picture: {
          large: ''
        },
        email: '',
        name: {
          first: '',
          last: ''
        }
      }
    };
  },
  mounted() {
    fetch("https://randomuser.me/api/")
      .then(response => response.json())
      .then(datos => (this.datos = datos.results[0]));
  },
};
</script>
