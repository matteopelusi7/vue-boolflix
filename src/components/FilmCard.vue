<template>

  <li class="list-item">
    <div class="img-poster">
      <img v-if="film.poster_path" :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
      <img v-else src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    </div>
    <div class="description">
      <p>Titolo: {{ film.title }}</p>
      <p>Titolo originale: {{ film.original_title }}</p>
      <img class="flag" :src="film.original_language" alt="">
      <p>Voto: {{ film.vote_average }}</p>
    </div>
  </li>
  
</template>

<script>

export default {
  name: 'FilmCard',
  props: {
    film: {
      type: Object,
      required: true
    }
  }
}

</script>

<style scoped lang="scss">

.flag {
  width: 15px;
}

.list-item {
  text-align: left;
  width: 20%;
  border: 2px solid white;
  color: white;
  position: relative;
  background-color: black;

  img {
    display: block;
  }

  p, .flag {
    padding: 5px 0;
    margin-left: 10px;
  }

  .description {
    position: absolute;
    top: 0;
    left: 0;
    padding-top: 10px;
  }

}

</style>
