<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
    props:['delay'], 
    data(){
        return {
            showBlock:false,
            timer:null, 
            reactTime:0
        }
    },
    // mounted is to run code before its rendor to the DOM
    mounted(){
        // console.log("mounted")
        setTimeout(()=>{
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        },this.delay)
    }, 
    methods:{
        startTimer(){
            this.timer = setInterval(()=> {
                this.reactTime += 10
            },10)
        }, 
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactTime)
            this.$emit('end',this.reactTime)
        }
    }
    // //updated is code that will run when the DOM is updated
    // updated(){
    //     console.log("updated")
    // }, 
    // // when the componet leaves this fires
    // unmounted(){
    // }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 10%;
    background-color: cadetblue;
    color: white;
    text-align: center;
    padding: 100px 0 ;
    margin: 40px auto;
}
</style>