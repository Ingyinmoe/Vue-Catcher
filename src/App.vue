<template>
  
  <div class="about-icon" @click="ShowAbout = true">
    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
      <path fill-rule="evenwodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM9 15a1 1 0 011-1h6a1 1 0 110 2h-6a1 1 0 01-1-1z" clip-rule="evenodd" />
    </svg>
  </div>

  <div class="about-game" v-if="ShowAbout">
    <div @click="ShowAbout = false">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd" />
      </svg>
    </div> 

    <h2>About This Game</h2>
    <span>How to play ?</span>
    <p>Tap the "Play" button and catch the box.</p>

    <div>
      <img src="./assets/logo.png" alt="">
      <p><span>Made With vue 3.</span></p>
    </div>

    <span>Create By Arkar Zaw.</span>

  </div>

  <h1>How fast can you catch me ?</h1>
  <button @click="ToShowBox" :disabled="ShowBox">Click to play</button>

  <box-modal v-if="ShowBox" :DelayTime="DelayTime" @EndGame="EndGame"/>

  <result-box :Score="Score" v-if="ShowResult"/>
</template>

<script>

import BoxModal from "./components/BoxModal.vue"
import ResultBox from "./components/ResultBox.vue"

export default {
  name: 'App',
  data(){
    return{
      ShowBox:false,
      DelayTime:null,
      Score:null,
      ShowResult:false,
      ShowAbout:false
    }
  },
  components: {
    BoxModal,
    ResultBox
  },
  methods:{
    ToShowBox(){
      this.ShowBox=true;
      this.ShowResult = false;
      this.DelayTime=1000+Math.random()*5000;    
    },
    EndGame(score){
      this.ShowResult = true ;
      this.Score = score;
      console.log(this.Score)
      this.ShowBox = false ;
    }
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  background: #42b883;
  border: none;
  outline: none;
  padding: 4px 10px;
  color: #fff;
  font-size: 16px;
  border-radius: 6px;
  transition: .4s;
}
button:hover{
  background: green;
}
button:disabled,
button[disabled]{
  background-color: #ff0000;
}

/* for about */
.about-icon svg,.about-game svg{
  width: 40px;
  color: #42b883;
  position: absolute;
  top: 20px;
  right: 20px;
  cursor: pointer;
}
.about-game{
  width: 100%;
  height: 100vh;
  position: absolute;
  background: #fff;
  top: 0;
  left: 0;
}
.about-game h2{
  margin-top: 60px;
}
.about-game img{
  width: 100px;
}
.about-game span{
  color: #42b883;
}
</style>
