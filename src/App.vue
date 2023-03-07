<script>
import AppHeader from "./components/AppHeader.vue";
import { store } from "./data/store";

export default {
  data() {
    return {
      store,
      title: "Hello Boolflix",
    };
  },

  components: { AppHeader },
};
</script>

<template>
  <header>
    <AppHeader />
  </header>
</template>

<style lang="scss">
body {
  background-color: black;
}
</style>
