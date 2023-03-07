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
          store.moviesList = response.data.results.filter(
            (film) => film.media_type == "movie"
          );
          // FILM = response.data.results[i];
          store.TvSeriesList = response.data.results.filter(
            (film) => film.media_type == "tv"
          );

          // **ALLA PRIMA RICERCA LA PAGINA E' BLOCCATA FINO AL REFRESH**

          // DEVO RESETTARE L'ARRAY:
          // store.moviesList = [];
          // store.TvSeriesList = [];

          // CICLO E PUSHO ( MEGLIO UN FILTER CHE E' GIA UN CICLO DI PER SE):
          // for (let i = 0; i < response.data.results.length; i++) {
          //   let mediaType = response.data.results[i].media_type;

          //   if (mediaType == "movie") {
          //     store.moviesList.push(response.data.results[i]);
          //   } else if (mediaType == "tv") {
          //     store.TvSeriesList.push(response.data.results[i]);
          //   }
          // }
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
    <div
      class="d-flex flex-row flex-wrap justify-content-center"
      v-if="store.moviesList.length"
    >
      <h2 class="movie">Movies:</h2>
      <MovieCard />
    </div>
    <div
      class="d-flex flex-row flex-wrap justify-content-center position-relative mt-5"
      v-if="store.TvSeriesList.length"
    >
      <h2 class="tv">Tv shows:</h2>
      <TvSeriesCard />
    </div>
    <div v-if="!store.moviesList.length && !store.TvSeriesList.length">
      <h2 class="start text-center mt-5">
        Cerca i tuoi film e serie tv preferiti...
      </h2>
    </div>
  </main>
</template>

<style lang="scss">
h2.movie {
  color: firebrick;
  height: fit-content;
  position: absolute;
  top: 10rem;
}

h2.tv {
  color: rgba(242, 159, 6);
  height: fit-content;
  position: absolute;
}

h2.start {
  color: firebrick;
}
</style>
