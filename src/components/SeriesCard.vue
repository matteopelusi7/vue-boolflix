<template>

  <li class="list-item">
    <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" alt="">
    <img v-else src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    <p>{{ serie.name }}</p>
    <p>{{ serie.original_name }}</p>
    <img class="flag" :src="serie.original_language" alt="">
    <p>{{ serie.vote_average }}</p>
  </li>
  
</template>

<script>

export default {
  name: 'SeriesCard',
  props: {
    serie: {
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
