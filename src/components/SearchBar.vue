<script>
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
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
  <div class="container input-group mb-3">
    <input
      type="text"
      class="form-control"
      placeholder="Recipient's username"
      aria-label="Recipient's username"
      aria-describedby="button-addon2"
      v-model="store.term"
      @keyUp.enter="searchedItem"
    />
    <button
      class="btn btn-outline-secondary"
      type="button"
      id="button-addon2"
      @click="searchedItem"
    >
      Search movies
    </button>
  </div>
</template>

<style lang="scss"></style>
