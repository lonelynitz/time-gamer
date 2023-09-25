<template>
  <h2>Reaction Time Gaming!!</h2>
  <button class="start-btn" :disabled="isPlaying" @click="startGame">Play</button>
  <BlockGame v-if="isPlaying" :delay="delay" @endGame="gameOver"/>
  <div v-if="showResult">
    <ResultGame :score="score"/>
  </div>
  <!--<p v-if="showResult">Reaction Time : {{ score }}ms</p> -->
</template>

<script>

import BlockGame from './components/BlockGame.vue' 
import ResultGame from './components/ResultGame.vue'

export default {
  name: 'App',
  components: { BlockGame , ResultGame },
  data(){
    return{
      isPlaying : false,
      delay : null,
      score : 0,
      showResult : false
    }
  },
  methods: {
    startGame(){
      this.delay = 1000 + Math.random() * 4000
      this.isPlaying = true
      console.log(this.delay);
    },
    gameOver(reactionTime){
      this.score = reactionTime
      this.showResult = true
      this.isPlaying = false
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

.start-btn {
  margin-top: 10px;
  padding: 10px 30px;
  transform: background-color 0.20ms;
  display: block;
  margin: 0 auto;

  
}


</style>
