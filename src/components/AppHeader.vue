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
          for (let i = 0; i < response.data.results.length; i++) {
            let mediaType = response.data.results[i].media_type;

            if (mediaType == "movie") {
              store.moviesList.push(response.data.results[i]);
            } else if (mediaType == "tv") {
              store.TvSeriesList.push(response.data.results[i]);
            }
          }
        });
    },
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
  <main class="row-cols-12">
    <div class="d-flex flex-row flex-wrap justify-content-center">
      <MovieCard />
    </div>
    <div class="d-flex flex-row flex-wrap justify-content-center">
      <TvSeriesCard />
    </div>
  </main>
</template>

<style lang="scss">
main {
  border: 2px dashed red;
}
</style>
