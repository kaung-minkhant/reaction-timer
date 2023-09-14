<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isStarted">Play</button>
  <Block v-if="isStarted" :delayMS="delayMS" @end="endGame" />
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isStarted: false,
      showResult: false,
      delayMS: null,
      score: null,
    }
  },
  methods: {
    start() {
      this.delayMS = 2000 + Math.random()*5000 // random delay between 2 sec to 7 sec
      this.isStarted = true
      this.showResult = false
    },
    endGame(reaction_time) {
      this.score = reaction_time
      this.isStarted = false
      this.showResult = true
    },
  },
  components: {
    Block,
    Results,
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

button {
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button:disabled {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
