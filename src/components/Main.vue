<template>
  <main>

    <ul class="list-wrapper">
      <FilmCard v-for="film in films" :key="film.id" :film="film" class="list-item" />
    </ul>

    <ul class="list-wrapper">
      <SeriesCard v-for="serie in series" :key="serie.id" :serie="serie" class="list-item" />
    </ul>

  </main>
</template>

<script>

import FilmCard from './FilmCard.vue'
import SeriesCard from './SeriesCard.vue'

export default {
  name: 'MainContent',
  components: {
    FilmCard,
    SeriesCard
  },
  props: {
    films: Array,
    series: Array
  },
}

</script>

<style scoped lang="scss">

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  background-color: grey;
  min-height: 100vh;

  }

  .list-wrapper{
    padding: 100px 0;
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
    justify-content: center;
}

</style>
