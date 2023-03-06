<script>
import SearchBar from "./SearchBar.vue";
import MovieCard from "./MovieCard.vue";
import TvSeriesCard from "./TvSeriesCard.vue";
import axios from "axios";
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  methods: {
    showResearch() {
      axios
        .get(
          `${store.endpoint}/search/multi?api_key=${store.myKey}&query=${store.term}`
        )
        .then((response) => {
          if (response.data.results[0].media_type === "movie") {
            store.moviesList = response.data.results;
          } else if (response.data.results[0].media_type === "tv") {
            store.TvSeriesList = response.data.results;
          }

          console.log(response.data.results);
        });
    },
  },

  computed: {
    flagChange() {
      if (store.moviesList[0].original_language == "en") {
        return store.moviesList[0].original_language == "gb";
      }
    },
  },

  // props: {
  //   lang: String,
  // },

  components: { SearchBar, MovieCard, TvSeriesCard },
};
</script>

<template>
  <header>
    <SearchBar
      placeholder="Find your favourite movie or Tv show..."
      @selectedMovie="showResearch"
    />
  </header>
  <main class="d-flex flex-wrap justify-content-center">
    <MovieCard />
    <TvSeriesCard />
  </main>
</template>

<style lang="scss">
main {
  border: 2px dashed red;
}
</style>
