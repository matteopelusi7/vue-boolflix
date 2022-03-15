<template>
  <main>

    <div>
      <input type="text" v-model="search">
      <button @click="getFilms">Cerca</button>
    </div>

    <ul class="list-wrapper">
      <li v-for="film in films" :key="film.id" class="list-item">
        <p>{{ film.title }}</p>
        <p>{{ film.original_title }}</p>
        <p>{{ film.original_language }}</p>
        <p>{{ film.vote_average }}</p>
      </li>
    </ul>

  </main>
</template>

<script>

import axios from 'axios'

export default {
  name: 'MainContent',
  data() {
    return {
      search: '',
      films: []
    }
  },
  methods: {
    getFilms: function () {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'f856965414a471b0188348e3edefb8c6',
          query: this.search,
          language: 'it-IT'
        }
      })
      .then( res => {
        this.films = res.data.results
      })
      .catch( error => {
        console.log(error.response)
      })
    }
  }
}

</script>

<style scoped lang="scss">

main {
  padding: 20px 0;

  .list-wrapper{
    padding: 10px 0;

    .list-item {
      padding: 15px 0;
    }
  }
}

</style>
