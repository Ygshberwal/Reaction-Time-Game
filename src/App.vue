<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying"> Play </button>
  <p v-if="!isPlaying && !showResults">A box will be shown below randomly, click on the box as quickly as you can.</p>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Result v-if="showResults" :score="score"/>

  
  
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'


export default {
  name: 'App',
  components: {Block, Result},
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResults:false
    }
  },
  methods:{
    start(){
      this.isPlaying=true,
      this.delay=2000+Math.random()*5000
      this.showResults=false

    },
    endGame(reactionTime){
      this.score=reactionTime
      this.isPlaying=false
      this.showResults=true
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

button{
  background-color: rgb(46, 198, 117);
  color: rgb(249, 247, 247);
  border: 1px solid;
  padding: 8px 16px;
  border-radius: 10px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
