<template>

  <li class="list-item">
    <img v-if="film.poster_path" :src="`https://image.tmdb.org/t/p/w342${film.poster_path}`" alt="">
    <img v-else src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    <p>{{ film.title }}</p>
    <p>{{ film.original_title }}</p>
    <img class="flag" :src="film.original_language" alt="">
    <p>{{ film.vote_average }}</p>
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
  padding: 15px 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
  justify-content: center;
  align-items: center;
  width: 20%;
  border: 1px solid salmon;
}

</style>
