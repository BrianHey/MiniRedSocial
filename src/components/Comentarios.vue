<template>
  <div id="Comentario" >
    <div class="comentario p-3" v-for="(comentario, index) in comentarios" :key="index">
      <img :src="comentario.imgSrc" width="50" alt="">
      <h5>{{comentario.name}}</h5>
      <h3>{{comentario.message}}</h3>
      <svg style="width:24px;height:24px" viewBox="0 0 24 24">
        <path
          fill="currentColor"
          d="M12,21.35L10.55,20.03C5.4,15.36 2,12.27 2,8.5C2,5.41 4.42,3 7.5,3C9.24,3 10.91,3.81 12,5.08C13.09,3.81 14.76,3 16.5,3C19.58,3 22,5.41 22,8.5C22,12.27 18.6,15.36 13.45,20.03L12,21.35Z"
        />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "Comentarios",
  props: ['comentarios'],
 };
</script>

<style  >
.comentario {
  text-align: left;
  width: 70%;
  border: solid 1px;
  border-radius: 15px;
}
.comentario >img{
  border-radius: 50%;
  
}
</style>
