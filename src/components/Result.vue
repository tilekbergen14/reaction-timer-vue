<template>
  <h3>{{ score }} ms for you, You are {{ ranking }}</h3>
</template>

<script>
export default {
  mounted() {
    if (this.score < 500) {
      this.ranking = "Master";
    } else if (this.score > 1000) {
      this.ranking = "Too bad";
    } else {
      this.ranking = "Not too bad";
    }
  },
  props: ["score"],
  data() {
    return {
      ranking: null,
    };
  },
};
</script>

<style>
</style>