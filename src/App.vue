<script>
import AppHeader from "./components/AppHeader.vue";

export default {
  data() {
    return {
      title: "Hello world",
    };
  },

  components: { AppHeader },
};
</script>

<template>
  <h1 class="text-danger">{{ title }}</h1>
  <AppHeader />
</template>

<style lang="scss"></style>
