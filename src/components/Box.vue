<template>
  <div class="box" v-if="showBox" @click="boxClicked">
    <h3>CLICK ME</h3>
  </div>
</template>

<script>
export default {
  props: ["delay"],

  data() {
    return {
      showBox: false,
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    boxClicked() {
      this.stopTimer();
      this.$emit("box-clicked", this.reactionTime);
    },

    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
        console.log(this.reactionTime)
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
    },
  },
};
</script>

<style scoped>
.box {
  width: 400px;
  height: 200px;
  background: #6add6a;
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
</style>