<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
  props: {
    delay: Number,
  },
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
      startTimer() {
          this.timer = setInterval(() => {
              this.reactionTime += 10;
          }, 10)
      },
      stopTimer() {
          clearInterval(this.timer);
          this.$emit('reactionEvent', this.reactionTime)
      }
  },
  beforeCreate() {
    console.log("1 beforeCreate");
  },
  created() {
    console.log("2 created");
  },
  beforeMount() {
    console.log("3 beforeMount");
  },
  mounted() {
    setTimeout(() => {
      this.$emit('showingBlock', true)
      this.showBlock = true;
      this.startTimer();
    }, this.delay);

    console.log("4 mounted");
  },
  beforeUpdate() {
    console.log("5 beforeUpdate");
  },
  updated() {
    console.log("6 updated");
  },
  activated() {
    console.log("7 activated");
  },
  deactivated() {
    console.log("8 deactivated");
  },
  beforeUnmount() {
    console.log("9 beforeUnmount");
  },
  unmounted() {
    console.log("10 unmounted");
  },
  errorCaptured() {
    console.log("11 errorCaptured");
  },
  renderTracked() {
    console.log("12 renderTracked");
  },
  renderTriggered() {
    console.log("13 renderTriggered");
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>