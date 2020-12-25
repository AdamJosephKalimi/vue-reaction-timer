<template>
  <div>
    <h1>How fast is your reaction time?</h1>
    <!-- disabled will disable the btn. It checks the binded data for the condition. -->
    <button @click="start" :disabled="isPlaying">Play</button>
    
      <!-- v-bind: || : - both enable us to bind data -->
      <Block v-if="isPlaying" :delay="delay"/>
    
  </div>
</template>

<script>
  import Block from './components/Block.vue'

export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      console.log(this.delay)
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
