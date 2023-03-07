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
  <ul class="m-3 mt-5" v-for="tvShow in store.TvSeriesList">
    <div class="flip-card">
      <div class="flip-inside">
        <div class="flip-front">
          <li>
            <img
              :src="`${store.imgpoint}${tvShow.poster_path}`"
              alt=""
              class="img-fluid"
            />
          </li>
        </div>
        <div class="flip-back">
          <li>
            Titolo: <br />
            {{ tvShow.name }}
          </li>
          <li>
            Titolo originale: <br />
            {{ tvShow.original_name }}
          </li>
          <li>
            Lingua originale:
            <img
              :src="flagChange(tvShow.original_language)"
              alt="flag"
              class="img-fluid flag-img"
            />
          </li>
          <li>
            Voto medio: <br />
            <div v-for="num in 5" :key="num" class="d-inline-block">
              <span v-if="num <= parseInt(tvShow.vote_average / 2)"
                ><font-awesome-icon icon="fa-solid fa-star" class="review-star"
              /></span>
            </div>
            <div
              v-for="num in 5 - parseInt(tvShow.vote_average / 2)"
              :key="num"
              class="d-inline-block"
            >
              <span v-if="(num = Math.ceil(parseInt(tvShow.vote_average / 2)))"
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
            {{ tvShow.overview }}
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
    padding: 0.2rem 0;
    .review-star {
      color: gold;
    }

    .empty-star {
      color: #bbb;
    }
  }
  // flipping cards
  .flip-card {
    background-color: rgba(242, 159, 6);
    width: 500px;
    height: 517px;
  }
  .flip-inside {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 10px 10px 20px 0 rgba(242, 159, 6, 0.934);
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
