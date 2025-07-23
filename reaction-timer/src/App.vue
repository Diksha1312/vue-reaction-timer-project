<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying" >Start Game</button>
    <BlockComp v-if="isPlaying" :delay="delay" />
  </div>
</template>
<script>

import BlockComp from './components/BlockComp.vue';
export default {
  name: 'App',
  components: { BlockComp },
  data() {
    return {
      isPlaying: false,
      delay: null,
    }
  },
  methods: {
    start() {
        this.delay = 2000 + Math.random() * 5000; // Random delay between 2 and 7 seconds
        this.isPlaying = true;
        console.log("this.delay", this.delay);
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
</style>
