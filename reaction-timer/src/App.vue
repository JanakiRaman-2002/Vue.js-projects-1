<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" class="buttonclass" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <!-- <p v-if="showResults">Reaction Time: {{ score }} ms</p> -->
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      console.log(this.delay)
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
  color: rgb(197, 178, 178);
  margin-top: 60px;
}
body {
  background: black;
}
button {
  width: 100px;
  background: rgb(94, 221, 100);
  height: 50px;
  padding: 2px auto;
  border-radius: 5px;
  cursor: pointer;
}
.buttonclass {
  font-family: Arial, Helvetica, sans-serif;
  font-weight: 500;
  font-size: 1rem;
}
</style>
