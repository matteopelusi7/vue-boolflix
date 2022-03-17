<template>

  <li class="list-item">
    <div class="img-poster">
      <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" alt="">
      <img v-else src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    </div>
    <div class="description">
      <p>{{ serie.name }}</p>
      <p>{{ serie.original_name }}</p>
      <img class="flag" :src="serie.original_language" alt="">
      <p> Voto: 
        <i v-for="(n, i) in 5" :key="i" class="fa-star" :class=" (n <= getVote) ? 'fa-solid' :  'fa-regular' "></i>
      </p>
    </div>
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
  },
  computed: {
    getVote: function() {
      return Math.ceil(this.serie.vote_average / 2)
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

  i {
    padding: 0 2px;
  }

  .fa-solid {
    color: gold;
  }

  .fa-regular {
    color: lightgrey;
  }

}

</style>
