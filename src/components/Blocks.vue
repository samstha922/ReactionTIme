<template>
    <div id="square" v-if="showBlock" @click="stopTimer">
        <p>Click here fast</p>
        {{delay}}
    </div>
</template>
<script>

export default {
    data(){
        return{
            showBlock: false,
            reactionTime: 0,
            timer: 0 
        }
    },
    props:['delay'],
    mounted(){
        console.log('components mounted');
        setTimeout(()=> {
            this.showBlock = true
            this.startTimer()     
        }, this.delay)
    },
    methods:{
        startTimer(){
            this.timer= setInterval(()=>{
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            // console.log('reaction time: '+this.reactionTime)
            this.$emit('endTime', this.reactionTime)
        }

    }
    // updated(){
    //     console.log('updated') 
    // },
    // unmounted(){
    //     console.log('unmounted')
    // }
}
</script>

<style scoped>
#square{
    position: absolute;
    top: 50%;
    left: 50%;
    margin-top: -100px;
    margin-left: -100px;
    width: 200px;
    height: 200px;
    background: orange; 
    color: black;
}
#square p{
    margin: 0;
    position: absolute;               /* 2 */
    top: 50%; 
    left: 20%;
}
</style>