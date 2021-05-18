<template>
  <div class="box" v-if="showBox" @click="boxClicked">
    <h3>CLICK ME</h3>
  </div>

  <div
    class="box box-cancel"
    :class="{ show: showBoxCancel == true }"
    v-if="!showBox"
    @click="boxCancel"
  >
    <h3>You click too soon.</h3>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  emits: ["box-clicked"],

  data() {
    return {
      showBox: false,
      showBoxCancel: false,
      timer: null,
      timeout: null,
      reactionTime: 0,
    };
  },

  mounted() {
    this.timeout = setTimeout(() => {
      this.showBox = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    boxClicked() {
      clearInterval(this.timer);
      this.$emit("box-clicked", this.reactionTime);
    },

    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    boxCancel() {
      this.showBoxCancel = true;
      clearTimeout(this.timeout);
      
      setTimeout(() => {
        this.$emit("box-clicked", this.reactionTime);
      }, 2000);
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
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.box-cancel {
  background: lightcoral;
  opacity: 0;
}

.show {
  opacity: 100;
}
</style>