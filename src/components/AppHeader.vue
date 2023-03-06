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
          if (response.data.results[0].media_type == "movie") {
            store.moviesList = response.data.results;
          } else if (response.data.results[0].media_type == "tv") {
            store.TvSeriesList = response.data.results;
          }

          console.log(response.data.results);
        });
    },
  },

  props: {
    lang: String,
  },

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
  <MovieCard />
  <TvSeriesCard />
</template>

<style lang="scss">
main {
  // height: 50vh;
}
</style>
