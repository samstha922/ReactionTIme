<template>
    <h1>Ninja Reaction Timer</h1>
    <button @click='start' :disabled='isStarted'>Start Game</button>
    <Blocks v-if="isStarted" :delay='delay' @endTime='endGame'/>
    <Results v-if="isEnd" :score ="score" :rank="rank"/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Blocks from './components/Blocks.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Blocks,
    Results
  },
  data(){
    return{
      isStarted: false,
      delay: null,
      score: 0,
      isEnd: false,
      rank:''
    }
  },
  methods:{
    start(){
      this.delay = 2000+Math.random()*5000
      this.isStarted = true
      this.isEnd=false
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.isEnd=true
      this.score=reactionTime
      if (this.score < 200){
        this.rank = "You're a ninja"
      }
      else if(this.score <=600){
        this.rank = "You've got fast reflexes"
      }
      else{
        this.rank = "You're really slow mate!!"
      } 
      console.log(this.score)
      this.isStarted=false
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
