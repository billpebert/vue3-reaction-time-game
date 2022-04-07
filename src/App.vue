<template>
  <h1>Reaction Timer Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @result="endGame" />
  <Results v-if="showResults" :scoreResults="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
      //console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime //reactionTime took from Block.vue $emit
      this.isPlaying = false
      this.showResults = true
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap');
*{
  font-family: 'Poppins', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
#app {
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button{
  background: #2e4cfa;
  padding: 16px 28px;
  border-radius: 8px;
  color: white;
  font-size: 18px;
  font-weight: 500;
  border: 0;
  cursor: pointer;
  transition: all .3s;
}

button[disabled]{
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
