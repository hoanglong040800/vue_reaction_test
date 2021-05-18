<template>
  <div>
    <h2 v-if="!isPlay">Result: {{ reactionTime }}ms</h2>

    <h2 v-if="!isPlay">Best result: {{ bestTime }}ms</h2>
  </div>
</template>

<script>
export default {
  props: ["reactionTime", "bestTime"],
};
</script>

<style scoped>
div {
  padding: 20px;
  border: 1px solid gray;
  border-radius: 10px;
  background: #b5e3ff;
  border: 1px solid #7ea8c2
}

h2 {
  margin: 20px 0;
  text-align: center;
}
</style>