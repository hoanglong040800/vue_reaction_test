<template>
  <div class="container">
    <main>
      <h1>Reaction Test</h1>

      <button :disabled="isPlay" @click="start">Play</button>

      <h3 v-if="!isPlay">Result: {{ reactionTime }}ms</h3>

      <h3 v-if="!isPlay">Best result: {{ bestTime }}ms</h3>

      <Box v-if="isPlay" :delay="delay" @box-clicked="boxClicked" />
    </main>
  </div>
</template>

<script>
import Box from "../components/Box";
import Result from "../components/Result";

export default {
  components: { Box },

  data() {
    return {
      isPlay: false,
      delay: null,
      reactionTime: 0,
      bestTime: 0,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000;
      this.isPlay = true;
    },

    boxClicked(reactionTime) {
      this.isPlay = false;
      this.reactionTime = reactionTime;

      if (this.bestTime == 0 || reactionTime < this.bestTime) {
        this.bestTime = reactionTime;
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  padding: 50px 0;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

button {
  width: 100px;
  height: 40px;
  margin: 20px 0;
  font-size: 1.2em;
  background: #c4c4c4;
  cursor: pointer;
}
</style>