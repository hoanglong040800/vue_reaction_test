<template>
  <div class="container">
    <main>
      <h1>Reaction Test</h1>

      <button v-if="!isPlay" @click="start">Play</button>

      <Result
        v-if="!isPlay"
        :reactionTime="reactionTime"
        :bestTime="bestTime"
      />

      <Box v-if="isPlay" :delay="delay" @box-clicked="boxClicked" />
    </main>
  </div>
</template>

<script>
import Box from "../components/Box";
import Result from "../components/Result";

export default {
  components: { Box, Result },

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

h1 {
  font-size: 3em;
  margin: 0 0 30px 0;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

button {
  width: 100px;
  height: 40px;
  margin: 0 0 20px 0;
  font-size: 1.2em;
  background: #fca910;
  border: 1px solid #b87f15;
  border-radius: 5px;
}
</style>