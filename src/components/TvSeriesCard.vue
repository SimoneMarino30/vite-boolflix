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
  <main class="d-flex flex-wrap justify-content-center">
    <ul class="row row-cols-1 m-3" v-for="tvShow in store.TvSeriesList">
      <li>Titolo: {{ tvShow.name }}</li>
      <li>Titolo originale:{{ tvShow.original_title }}</li>
      <li>
        Lingua originale:
        <img
          :src="`${store.flagpoint}${tvShow.original_language}.png`"
          alt="flag"
          class="img-fluid flag-img"
        />
      </li>

      <li>Voto medio: {{ tvShow.vote_average }}</li>
    </ul>
  </main>
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

main {
  border: 2px dashed red;
}
</style>
