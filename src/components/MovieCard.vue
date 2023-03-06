<script>
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  // components: {
  //   MyComponent,
  // },
};
</script>

<template>
  <ul class="row row-cols-1 md-3 m-3" v-for="movie in store.moviesList">
    <li>Titolo: {{ movie.title }}</li>
    <li>Titolo originale:{{ movie.original_title }}</li>
    <li>
      Lingua originale:
      <img
        :src="`${store.flagpoint}${movie.original_language}.png`"
        alt="flag"
        class="img-fluid flag-img"
      />
    </li>
    <li>MOVIEEEEEEEEE</li>
    <li>Voto medio: {{ movie.vote_average }}</li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
}

.row {
  border: 2px dashed blue;
  width: calc(100% / 4);
  height: 450px;
}
</style>
