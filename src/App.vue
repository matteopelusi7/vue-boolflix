<template>
  <div id="app">
    <MainHeader @search="getSearch" />
    <MainContent :films="films" :series="series" />
  </div>
</template>

<script>

import axios from 'axios'
import MainContent from './components/Main.vue'
import MainHeader from './components/Header.vue'

export default {
  name: 'App',
  components: {
    MainContent,
    MainHeader
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
              el.original_language = require('../src/assets/img/england.webp')
              break;
            case 'it':
              el.original_language = require('../src/assets/img/italia.webp')
              break;
            case 'es':
              el.original_language = require('../src/assets/img/spagna.webp')
            break;
            default:
              el.original_language = require('../src/assets/img/default.webp')
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
              el.original_language = require('../src/assets/img/england.webp')
              break;
            case 'it':
              el.original_language = require('../src/assets/img/italia.webp')
              break;
            case 'es':
              el.original_language = require('../src/assets/img/spagna.webp')
            break;
            default:
              el.original_language = require('../src/assets/img/default.webp')
          }

        });

      })
      .catch( error => {
        console.log(error.response)
      })

    },

    getSearch : function(search) {
      this.search = search
      this.getFilms()
    }
  
  },
}

</script>

<style lang="scss">

@import './assets/scss/common.scss';
@import '~@fortawesome/fontawesome-free/css/all.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

</style>
