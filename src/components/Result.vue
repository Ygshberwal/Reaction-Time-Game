<template>
<p>Reaction Time: {{ score }} ms</p>
<p class="rank">{{ rank }}</p>
</template>

<script>
export default{
    props:['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if (this.score<300){
            this.rank='Ninja Fingers'
        }else if (this.score<=400){
            this.rank='Rapid Reflexes'
        } else{
            this.rank="Snail pace.."
        }
    }

}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: aqua;
    font-weight: bold;
}

</style>