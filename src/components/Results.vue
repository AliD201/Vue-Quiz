<template>
  <div class="result">
    <div class="title">{{results[resultIndex].title}} - total correct: {{totalCorrect}}!</div>
    <div class="desc">{{results[resultIndex].desc}}</div>
  </div>
</template>

<script>
export default {
props: {
    totalCorrect: Number,
    results:Array
},
computed:{
    resultIndex(){
        let index = this.results.findIndex((result) =>{
            return ( this.totalCorrect >= result.min 
            && this.totalCorrect <= result.max)
        })

        return index;
    }
}
}
</script>

<style>
</style>