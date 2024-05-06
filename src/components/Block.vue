<template>
  <h3 v-if="!showModal">Loading...</h3>
  <div v-if="showModal" class="block" @click="stopTimer">Block</div>
</template>

<script>
export default {
  mounted() {
    setTimeout(() => {
      this.showModal = true;
      this.startTimer();
    }, this.delay);
  },
  props: ["delay"],
  data() {
    return {
      showModal: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  background-color: crimson;
  padding: 16px;
  color: white;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>