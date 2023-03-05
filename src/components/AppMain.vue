<script>
// import MovieCard from "./MovieCard.vue";
// import axios from "axios";
import { store } from "../data/store.js";

export default {
  data() {
    return {
      // store,
      // moviesList: [],
    };
  },

  // // chiamata API
  // created() {
  //   axios
  //     .get(
  //       `${store.endpoint}/search/multi?api_key=${store.myKey}&query=${store.term}`
  //     )

  //     .then((response) => {
  //       this.moviesList = response.data.results;
  //       console.log(response.data.results);
  //       console.log("################");
  //       console.log(this.moviesList);
  //     });
  // },

  // components: { MovieCard },
};
</script>

<template>
  <!-- <main>
    <ul class="row row cols-2 ms-5" v-for="movie in this.moviesList">
      <li>{{ movie.title }}</li>
      <li>{{ movie.name }}</li>

      <li>{{ movie.original_title }}</li>
      <li>
        <img
          :src="`${store.flagpoint}${movie.original_language}.png`"
          alt="flag"
          class="img-fluid flag-img"
        />
      </li>

      <li>{{ movie.original_language }}</li>
      <li>{{ movie.vote_average }}</li>
    </ul>
  </main> -->
</template>
<!-- <MovieCard /> -->
<style lang="scss">
// main {
//   height: 50vh;
//   .flag-img {
//     border: 3px dashed green;
//     height: 50px;
//     width: 50px;
//   }
// }
</style>
