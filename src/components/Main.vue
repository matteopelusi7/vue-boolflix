<template>
  <main>

    <div class="input">
      <h1 class="title">Boolflix</h1>
      <div>
        <input type="text" v-model="search">
        <button @click="getFilms">Cerca</button>
      </div>
    </div>

    <ul class="list-wrapper">
      <FilmCard v-for="film in films" :key="film.id" :film="film" class="list-item" />
    </ul>

    <ul class="list-wrapper">
      <SeriesCard v-for="serie in series" :key="serie.id" :serie="serie" class="list-item" />
    </ul>

  </main>
</template>

<script>

import axios from 'axios'
import FilmCard from './FilmCard.vue'
import SeriesCard from './SeriesCard.vue'

export default {
  name: 'MainContent',
  components: {
    FilmCard,
    SeriesCard
  },
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  background-color: grey;
  min-height: 100vh;

  }

  .input {
    background-color: black;
    display: flex;
    gap: 15px;
    justify-content: space-between;
    padding: 20px 30px;
    align-items: center;
    position: fixed;
    top: 0;
    width: 100%;

    .title {
      text-transform: uppercase;
      color: red;
    }

    input {
      padding: 5px 15px;
      border-radius: 8px;
    }

    button {
      margin-left: 20px;
      padding: 5px 15px;
      border: none;
      background-color: red;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
  }

  .list-wrapper{
    padding: 100px 0;
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
    justify-content: center;
}

</style>
