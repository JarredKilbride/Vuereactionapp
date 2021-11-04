<template>
<div id="header">
 <h1 >Reaction Timeer</h1>
 <!-- this disabled stops the use of the button while the game is being played. -->
 <button @click="start" :disabled="isPlaying">Play</button>
 <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
 <Result v-if="showResult" :score="score"/>
 </div>
</template>

<script>
import Block  from './components/Block'
import Result from './components/Result'
export default {
  name: 'App',
  components: { Block , Result},
  data(){
    return {
      isPlaying: false,
      delay:0, 
      score:null, 
      showResult: false
    }
  }, 
  methods: {
    start() {
      this.showResult = false
      // give a rendom in ms of 2 - 7 sec
      this.delay = 2000 + Math.random() * 5000
      //when user start this show that the game is being played
      this.isPlaying = true
    }, 
    endGame(r){
      this.score = r
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#header {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  margin: 10px;
  padding: 10px 20px;
  border-radius: 10px;
  background: lightslategray;
  color: white;
  cursor: pointer;
  border: none;
}

button[disabled] {
  opacity: .2;
}
</style>
