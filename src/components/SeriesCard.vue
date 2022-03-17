<template>

  <li class="list-item">
    <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w342${serie.poster_path}`" alt="">
    <img v-else src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
    <div class="description">
      <p>{{ serie.name }}</p>
      <p>{{ serie.original_name }}</p>
      <img class="flag" :src="serie.original_language" alt="">
      <p> Voto: 
        <i v-for="(n, i) in 5" :key="i" class="fa-star" :class=" (n <= getVote) ? 'fa-solid' :  'fa-regular' "></i>
      </p>
      <p>Overview: {{ serie.overview }}</p>
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
  cursor: pointer;

  &:hover {

    .description {
      display: block;
      position: absolute;
      top: 0;
      width: 100%;
    }

  }
  
  img {
    display: block;
  }

  p, .flag {
    padding: 5px 0;
    margin-left: 10px;
  }

  .title-info {
    font-weight: 700;
  }

  .description {
    display: none;
    background-color: rgba(0, 0, 0, 0.8);
    height: 100%;
    padding: 10px;
    overflow-y: auto;
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
