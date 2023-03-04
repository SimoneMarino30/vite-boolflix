<script>
import SearchBar from "./SearchBar.vue";
import { store } from "../data/store.js";

export default {
  data() {
    return {
      store,
    };
  },

  components: { SearchBar },
};
</script>

<template>
  <header>
    <SearchBar @selectedMovie="" />
  </header>
</template>

<style lang="scss"></style>
