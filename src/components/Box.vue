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
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBox = true;
    }, this.delay);
  },

  methods: {
    boxClicked() {
      this.$emit("box-clicked");
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