<template>
  <h1>Reaction Timer</h1>
  <button type="button" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @reactionEvent="reactionMethod" @showingBlock="handleShowingBlock" />
  <Result v-if="showResult" :score="score" />
  <h1 v-if="isPlaying && !isShowingBlock">Get Ready...</h1>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
      isShowingBlock: false,
    }
  },
  methods: {
    start() {
      this.delay = Math.floor(2000 + Math.random() * 5000);
      this.isPlaying = true;
      this.showResult = false;
      this.score = null;
      this.isShowingBlock = false;
    },
    reactionMethod(reactionEvent) {
      this.score = reactionEvent;
      this.isPlaying = false;
      this.showResult = true;
    },
    handleShowingBlock() {
      this.isShowingBlock = true;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  cursor: pointer;
  padding: 10px 50px;
  background: #0faf87;
  color: #fff;
  border: none;
  border-radius: 5px;
  font-weight: bold;
}
button:disabled {
  cursor: not-allowed;
  opacity: 0.2;
}
</style>
