<template>
  <h2>TQ's Reaction Timer</h2>
  <button @click="start" :disabled="isPlaying" :class="{ disabled: isPlaying }">
    Start
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false;
    },
    endGame(score) {
      this.score = score;
      this.showResult = true;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  padding: 8px 24px;
  margin-bottom: 16px;
  background-color: dodgerblue;
  border: 0;
  border-radius: 8px;
  color: white;
  font-size: 16px;
}
.disabled {
  background-color: gray;
}
</style>
