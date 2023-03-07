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
      if (nation == "hy") return "https://flagcdn.com/16x12/am.png";

      return `${store.flagpoint}${nation}.png`;
    },
  },
  // components: {
  //   MyComponent,
  // },
};
</script>

<template>
  <ul class="m-3" v-for="movie in store.moviesList" text="Movies:">
    <div class="flip-card">
      <div class="flip-inside">
        <div class="flip-front">
          <li>
            <img
              :src="`${store.imgpoint}${movie.poster_path}`"
              alt=""
              class="img-fluid"
            />
          </li>
        </div>
        <div class="flip-back">
          <li>
            Titolo: <br />
            {{ movie.title }}
          </li>
          <li>
            Titolo originale: <br />
            {{ movie.original_name }}
          </li>
          <li>
            Lingua originale:
            <img
              :src="flagChange(movie.original_language)"
              alt="flag"
              class="img-fluid flag-img"
            />
          </li>
          <li>
            Voto medio: <br />
            <div v-for="num in 5" :key="num" class="d-inline-block">
              <span v-if="num <= parseInt(movie.vote_average / 2)"
                ><font-awesome-icon icon="fa-solid fa-star" class="review-star"
              /></span>
            </div>
            <div
              v-for="num in 5 - parseInt(movie.vote_average / 2)"
              :key="num"
              class="d-inline-block"
            >
              <span v-if="(num = Math.ceil(parseInt(movie.vote_average / 2)))"
                ><font-awesome-icon icon="fa-solid fa-star" class="empty-star"
              /></span>
              <span v-else="(num = 0)"
                ><font-awesome-icon
                  :key="num"
                  icon="fa-solid fa-star"
                  class="empty-star"
              /></span>
            </div>
          </li>
          <li>
            Trama: <br />
            {{ movie.overview }}
          </li>
        </div>
      </div>
    </div>
  </ul>
</template>

<style lang="scss" scoped>
ul {
  list-style: none;
  background-color: black;

  li {
    background-color: black;
    .review-star {
      color: gold;
    }
  }
  .flip-card {
    background-color: firebrick;
    width: 500px;
    height: 520px;
  }
  .flip-inside {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 10px 10px 20px 0 rgba(242, 6, 6, 0.934);
  }

  .flip-card:hover .flip-inside {
    transform: rotateY(180deg);
  }

  .flip-front,
  .flip-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
  }

  .flip-front {
    background-color: black;
    color: black;
  }

  .flip-back {
    background-color: black;
    color: white;
    transform: rotateY(180deg);
  }
}
</style>
