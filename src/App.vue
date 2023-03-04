<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

import { store } from "./data/store";

export default {
  data() {
    return {
      store,
      title: "Hello Boolflix",
    };
  },

  components: { AppHeader, AppMain },
};
</script>

<template>
  <h1 class="container text-danger">{{ title }}</h1>
  <header>
    <AppHeader />
    <hr />
    <AppMain />
  </header>
</template>

<style lang="scss"></style>
