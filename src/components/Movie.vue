<template>
  <div class="movie" @click="setActiveMovie">
  <div class="media">
    <!-- NOTE props can be accessed directly within the template by name -->
    <img class="mr-3" :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`" alt="Movie Poster">
    <div class="media-body">
      <h5 class="mt-0">{{movie.title}}</h5>
      <p>Score: {{movie.vote_average}}</p>
    </div>
</div>
  </div>
</template>

<script>
import { movieService } from '../services/MovieService'

export default {
  name: 'movie',
  // NOTE props are passed to an object with a defined type
  props: {
    movie: Object
  },
  // NOTE if you want props in setup must pass param
  setup(props) {
    return {
      setActiveMovie() {
        // NOTE to access the props they can be gotten from the props parameter
        movieService.setActive(props.movie)
      }
    }
  },
  components: {}
}
</script>

<style scoped>
img {
  width: 100px;
}
</style>
