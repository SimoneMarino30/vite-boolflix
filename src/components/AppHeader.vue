<script>
import SearchBar from "./SearchBar.vue";
import axios from "axios";
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
      moviesList: [],
    };
  },

  methods: {
    showResearch() {
      axios
        .get(
          `${store.endpoint}/search/multi?api_key=${store.myKey}&query=${store.term}`
        )
        .then((response) => {
          this.moviesList = response.data.results;
          console.log(this.moviesList);
          console.log(response.data.results);
        });
    },
  },

  props: {
    lang: String,
  },

  components: { SearchBar },
};
</script>

<template>
  <header>
    <SearchBar
      placeholder="Find your favourite movie or Tv show..."
      @selectedMovie="showResearch"
    />
  </header>
  <main>
    <ul
      class="row row cols-2 ms-5 d-inline-block"
      v-for="movie in this.moviesList"
    >
      <li v-if="movie.media_type == 'movie'">Titolo: {{ movie.title }}</li>
      <li v-else>Titolo: {{ movie.name }}</li>

      <li v-if="movie.media_type == 'movie'">
        Titolo originale:{{ movie.original_title }}
      </li>
      <li>
        Lingua originale:
        <img
          :src="`${store.flagpoint}${movie.original_language}.png`"
          alt="flag"
          class="img-fluid flag-img"
        />
      </li>
      <!-- v-if="movie.original_language === 'en' ? 'gb' : 'Not found'" -->
      <!-- ********************************************************************** -->
      <!-- <li>
        Lingua originale:
        {{ (movie.original_language = "en" ? "gb" : "it") }}
      </li> -->
      <li>Voto medio: {{ movie.vote_average }}</li>
    </ul>
  </main>
</template>

<style lang="scss">
header {
  // background-color: black;
}

main {
  height: 50vh;
  .flag-img {
    border: 3px dashed green;
    height: 50px;
    width: 50px;
  }

  ul {
    list-style: none;
  }
}
</style>
