<script>
import SearchBar from "./SearchBar.vue";
export default {
  data() {
    return {};
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
