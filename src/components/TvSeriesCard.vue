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
  <ul class="row row-cols-1 md-3 m-3" v-for="tvShow in store.TvSeriesList">
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
    <li>SERIEEEEEEEEEEEE</li>
    <li>Voto medio: {{ tvShow.vote_average }}</li>
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

main {
  border: 2px dashed red;
}
</style>
