<template>
  <p>Reaction Time: {{ scoreResults }} </p>
  <h4>{{ rank }}</h4>
</template>

<script>
export default {
    props: ['scoreResults'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.scoreResults < 250){
            this.rank = 'Ninja Fingers'
        }else if(this.scoreResults < 400){
            this.rank = 'Rapid Reflexes'
        }else{
            this.rank = 'Turtle Man!'
        }
    }
}
</script>

<style>

</style>