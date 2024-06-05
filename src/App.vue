<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Result v-if="showResult" :score="score"></Result>
</template>

<script>
import Block from "@/components/Block.vue";
import Result from "@/components/Result.vue";
export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      delay: null,
      score : null,
      showResult : false,
    }
  },
  components: {
    Result,
    Block
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000
      this.showResult = false;
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
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
</style>
