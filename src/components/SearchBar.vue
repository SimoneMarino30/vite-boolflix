<script>
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  props: {
    placeholder: String,
  },

  emits: ["selectedMovie"],

  methods: {
    searchedItem() {
      this.$emit("selectedMovie", store.term);
      console.log("researched " + store.term);
      store.term = "";
    },
  },
};
</script>

<template>
  <div class="d-flex justify-content-between mt-5">
    <div class="container input-group mb-3">
      <img src="../assets/img/Boolflix.png" alt="logo" class="img-fluid" />
      <input
        type="text"
        class="form-control"
        :placeholder="placeholder || 'Search...'"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
        v-model="store.term"
        @keyup.enter="searchedItem"
      />
      <button
        class="btn btn-danger"
        type="button"
        id="button-addon2"
        @click="searchedItem"
      >
        Search
      </button>
    </div>
  </div>
</template>

<style lang="scss">
input,
button {
  height: 50px;
  margin-top: 15px;
}
</style>
