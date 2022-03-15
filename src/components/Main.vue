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
        <img :src="film.original_language" alt="">
        <p>{{ film.vote_average }}</p>
      </li>
    </ul>

    <ul class="list-wrapper">
      <li v-for="serie in series" :key="serie.id" class="list-item">
        <p>{{ serie.name }}</p>
        <p>{{ serie.original_name }}</p>
        <img :src="serie.original_language" alt="">
        <p>{{ serie.vote_average }}</p>
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
      films: [],
      series: []
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

        this.films.forEach( el => {

          switch(el.original_language) {
            case 'en':
              el.original_language = require('../assets/img/england.webp')
              break;
            case 'it':
              el.original_language = require('../assets/img/italia.webp')
              break;
            case 'es':
              el.original_language = require('../assets/img/spagna.webp')
            break;
            default:
              el.original_language = require('../assets/img/default.webp')
          }

        });

      })
      .catch( error => {
        console.log(error.response)
      })

      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: 'f856965414a471b0188348e3edefb8c6',
          query: this.search,
          language: 'it-IT'
        }
      })
      .then( res => {
        this.series = res.data.results

        this.series.forEach( el => {

          switch(el.original_language) {
            case 'en':
              el.original_language = require('../assets/img/england.webp')
              break;
            case 'it':
              el.original_language = require('../assets/img/italia.webp')
              break;
            case 'es':
              el.original_language = require('../assets/img/spagna.webp')
            break;
            default:
              el.original_language = require('../assets/img/default.webp')
          }

        });

      })
      .catch( error => {
        console.log(error.response)
      })

    }
  
  },

}

</script>

<style scoped lang="scss">

main {
  padding: 20px 0;

  .list-wrapper{
    padding: 10px 0;

    img {
      width: 15px;
    }

    .list-item {
      padding: 15px 0;
    }
  }
}

</style>
