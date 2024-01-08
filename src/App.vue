<template>
  <div>
    <h1>Vue Reaction Timer</h1>
    <p>Come on down and test your reactions!</p>
  </div>
  <div>
    <button @click="start" :disabled="isPlaying">Play</button>
  </div>
  <Results v-if="showResults" :score="score" />
  <!-- <div v-if="showResults">
    <p>Reaction time : {{ score }}</p>
  </div> -->
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return { isPlaying: false, delay: null, score: null, showResults: false };
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 2000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(time) {
      this.score = time;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
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
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 0.5px;
  cursor: pointer;
  margin: 10px;
  font-weight: 750;
}
button[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
