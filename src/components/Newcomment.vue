<template>
  <div id="Newcomment">
    <textarea v-model="message" class="form-control" name id cols="30" rows="2"></textarea>
    <button @click="newComment" class="btn btn-info w-100">Enviar Comentario</button>
  </div>
</template>

<script>
export default {
  name: "NewComment",
  data() {
    return {
      message: ""
    };
  },
  methods: {
    newComment() {
      this.$emit("newcoment", this.message);
      this.message = "";
    },
  }
};
</script>

<style>
#Newcomment {
  width: 80%;
  margin: auto;
}
</style>
