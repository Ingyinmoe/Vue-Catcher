<template>
  <div class="box" v-if="ShowModal" @click="StopTimer">
      <p>Catch Me</p>
  </div>
</template>

<script>
export default {
    props:['DelayTime'],
    data(){
        return {
            ShowModal:false,
            score:0,
            timer:null
        }
    },
    mounted(){
        setTimeout(() => {
            this.ShowModal=true
            this.StartTimer()
        }, this.DelayTime);
    },
    methods:{
        StartTimer(){
            this.timer = setInterval(() => {
                            this.score += 1
                        }, 1);
        },
        StopTimer(){
            clearInterval(this.timer);
            this.ShowModal = false ;
            this.$emit("EndGame",this.score);
        }
    }
}
</script>

<style>
.box{
    background: #42b883;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 400px;
    height: 200px;
    margin: 20px auto;
    border-radius: 12px;
    cursor: pointer;
}
.box p{
    font-size: 20px;
    font-weight: 600;
}
</style>