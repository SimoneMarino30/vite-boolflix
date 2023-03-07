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
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@300&display=swap");

body {
  background-color: black;
  font-family: "Kanit", sans-serif;
}
</style>
