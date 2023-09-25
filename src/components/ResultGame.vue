<template>
  <p>Reaction Time : {{ score }}ms</p>
  <p>{{ rank }}</p>
</template>

<script>
export default {
  props : ['score'],
  data(){
    return{
      rank : null
    }
  },
  mounted() {
    if(this.score < 250){
      this.rank = 'Your are Fast!'
    }else if (this.score < 450){
      this.rank = 'Good reflexes'
    }else{
      this.rank = 'Better luck next time!!'
    }
  }
}
</script>

<style>

</style>