<template>
  <div>
    <h1>How fast is your reaction time?</h1>
    <!-- disabled will disable the btn. It checks the binded data for the condition. -->
    <button @click="start" :disabled="isPlaying">Play</button>
    <!-- v-bind: || : - both enable us to bind data -->
    <Block v-if="isPlaying" :delay="delay" @endTimer="endGame"/>
    <!-- only display Results if reactionTime == true. Pass reactionTime to Results component -->
    <Results v-if="showResults" :reactionTime="reactionTime"/>
    
    
  </div>
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
      reactionTime: 0,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    // this argument keyword can be whatever you want. It is bringing in the data from
    // Block.vue
    endGame(reactionTime) {
      // console.log("endGame reaction time", reactionTime)
      console.log("Game ended")
      this.reactionTime = reactionTime
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
  color: #444;
  margin-top: 60px;
}
button {
  background:#0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
