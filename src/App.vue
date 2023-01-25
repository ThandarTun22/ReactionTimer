<template>
  <h1>How fast can u catch me?</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
     <BlockComp :delay="delay" @endGame="endGame"/>
  </div>
  <div v-if="end">
    <ResultComp :score="score"/>
  </div>
</template>

<script>
import BlockComp from "./components/BlockComp.vue"
import ResultComp from "./components/ResultComp.vue"

export default {
  name: 'App',
  components: {
    BlockComp,
    ResultComp
  },data(){
    return{
      isPlaying : false,
      delay : null,
      score : 0,
      end: false
    }
  },
  methods : {
    start(){
      this.isPlaying = true
      this.delay = 2000+Math.random()*5000
      
    },
    endGame(score){
      this.score = score;
      this.isPlaying = false; //endGame
      this.end = true
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
