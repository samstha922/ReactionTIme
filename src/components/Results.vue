<template>
<div id="score">
    <p>Your score is: {{score}}</p>
    <br>
    <p>{{rank}}</p>
</div>    
</template>

<script>
export default {
    props:['score','rank'],
    data(){
        return{
        }
    }

}
</script>
<style scoped>
    #score{
        background: red;
        color: white;
        width: 200px;
        height: 200px;
    }
</style>