<template>
  <div class="result">
      <h2>Your Reation Time</h2>
      <p>{{rank}}</p>
      <p> {{score}} ms</p>
  </div>
</template>

<script>
export default {
props: ['score'], 
data(){
    return {
        rank:null
    }
}, 
mounted() {
    if(this.score < 250) {
        this.rank = "Wow you're fast"
    }
    else if (this.score < 400) {
        this.rank = "Not bad"
    }
    else {
        this.rank  = "Got to work on this..."
    }
}
}
</script>

<style>
.result {
    width: 400px;
    border: black solid 1px;
    border-radius: 10%;
    background-color: rgb(238, 236, 236);
    color: rgb(0, 0, 0);
    text-align: center;
    padding: 100px 0 ;
    margin: 40px auto;
}
</style>