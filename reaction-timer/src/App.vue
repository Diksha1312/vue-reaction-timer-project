<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying" >Start Game</button>
    <BlockComp v-if="isPlaying" :delay="delay" @end="end" />
    <ResultsComp v-if="showResults" :score="score" />
  </div>
</template>

<script>

import BlockComp from './components/BlockComp.vue';
import ResultsComp from './components/ResultsComp.vue';
export default {
  name: 'App',
  components: { BlockComp, ResultsComp },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
        this.delay = 2000 + Math.random() * 5000 // Random delay between 2 and 7 seconds
        this.isPlaying = true
        console.log("this.delay", this.delay)
        this.showResults = false
      },
      end(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
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
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 20px;       
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
  font-size: 16px;
}
button[disabled] {
  opacity: 0.5;
  cursor: not-allowed;
}  
</style>
