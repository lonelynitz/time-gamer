<template>
  <button class="block" v-if="showgame" @click="stopTimer"></button>
  <!--<div class="block1"  v-if="showgame"  @click="stopTimer">
  </div>
  <div class="block2"  v-if="showgame"  @click="stopTimer">
  </div> -->
</template>

<script>
export default {
  props : ['delay'],
  data(){
    return{
      showgame : false,
      timer : null,
      reaction : 0
    }
  },
  mounted(){
    setTimeout(() => {
      this.showgame = true
      this.startTimer()
    }, this.delay);
  },
  methods : {
    startTimer(){
      this.timer = setInterval(() => {
        this.reaction +=10
      }, 10);
    },
    stopTimer(){
      clearInterval(this.timer)
      this.$emit('endGame',this.reaction)
    }
  }
}
</script>

<style>
.block{
  width: 300px;
  height: 200px;
  border-radius: 20px;
  display: flex;
  align-items: center;
  background-color: chartreuse ;
  text-align: center;
  display: inline-block;
  margin-top: 60px ;
  margin-right: 20px;
  border: none;
}
/*.block{
  background-color: cadetblue;
}
.block1{
  background-color: brown ;
}
.block2{
  background-color: chartreuse ;
}*/

</style>