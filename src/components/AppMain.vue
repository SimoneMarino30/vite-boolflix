<script>
import MovieCard from "./MovieCard.vue";
import axios from "axios";
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  // chiamata API
  created() {
    axios
      .get(
        `${store.endpoint}/search/movie?api_key=${store.myKey}&query=${store.term}`
      )
      //   language: italian
      // .get(
      //   "`https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${term}&original_language=it`"
      // )
      .then((response) => {
        console.log(response.data.results);
        store.moviesList = response.data.results;
      });
  },

  components: { MovieCard },
};
</script>

<template>
  <main>
    <div class="row row cols-2" v-for="movie in store.moviesList">
      <h3>{{ movie.title }}</h3>
      <p>{{ movie.original_title }}</p>
      <img
        :src="`${store.flagpoint}${movie.original_language}.png`"
        alt="flag"
        class="img-fluid flag-img"
      />
      <p>{{ movie.original_language }}</p>
      <p>{{ movie.vote_average }}</p>
      <MovieCard />
    </div>
  </main>
</template>

<style lang="scss">
main {
  height: 50vh;
  .flag-img {
    border: 3px dashed green;
    height: 50px;
    width: 50px;
  }
}
</style>
