<script>
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  methods: {
    flagChange(nation) {
      if (nation == "en") return "https://flagcdn.com/16x12/gb.png";
      if (nation == "ja") return "https://flagcdn.com/16x12/jp.png";
      if (nation == "zh") return "https://flagcdn.com/16x12/cn.png";
      if (nation == "ko") return "https://flagcdn.com/16x12/kr.png";

      return `${store.flagpoint}${nation}.png`;
    },
  },
  // components: {
  //   MyComponent,
  // },
};
</script>

<template>
  <ul class="row m-3" v-for="movie in store.moviesList">
    <!-- <h1>Movies:</h1> -->
    <li>Titolo: {{ movie.title }}</li>
    <li>Titolo originale:{{ movie.original_title }}</li>
    <li>
      Lingua originale:
      <img
        :src="flagChange(movie.original_language)"
        alt="flag"
        class="img-fluid flag-img"
      />
    </li>
    <li>
      Voto medio:
      <div v-for="num in 5" :key="num" class="d-inline-block">
        <span v-if="num <= parseInt(movie.vote_average / 2)">
          <font-awesome-icon icon="fa-solid fa-star" />
        </span>
      </div>
    </li>

    <li>
      <img
        :src="`${store.imgpoint}${movie.poster_path}`"
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
  border: 2px dashed blue;
  width: calc(100% / 6);
  // background-color: #000;
  .poster-img {
    height: 450px;
  }
}
</style>
