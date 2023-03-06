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
  <ul class="row m-3" v-for="tvShow in store.TvSeriesList">
    <!-- <h1>TV shows:</h1> -->
    <li>Titolo: {{ tvShow.name }}</li>
    <li>Titolo originale:{{ tvShow.original_name }}</li>
    <li>
      Lingua originale:
      <img
        :src="`${store.flagpoint}${tvShow.original_language}.png`"
        alt="flag"
        class="img-fluid flag-img"
      />
    </li>
    <li>Voto medio: {{ tvShow.vote_average }}</li>
    <li>
      <img
        :src="`${store.imgpoint}${tvShow.poster_path}`"
        alt=""
        class="img-fluid poster-img"
      />
    </li>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
}

.row {
  border: 2px dashed green;
  width: calc(100% / 4);

  .poster-img {
    height: 450px;
  }
}

main {
  border: 2px dashed red;
}
</style>
