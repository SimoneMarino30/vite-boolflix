<script>
export default {
  data() {
    return {
      term: "",
    };
  },
  emits: ["selectedMovie"],
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
      v-model="term"
      @click="$emit('selectedMovie')"
    />
    <button class="btn btn-outline-secondary" type="button" id="button-addon2">
      Search movies
    </button>
  </div>
</template>

<style lang="scss"></style>
