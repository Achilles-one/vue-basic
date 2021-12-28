<template>
<p>Reaction Time: {{ score }} ms</p>
<p class="rank">{{ rank }}</p>
  
</template>

<script>
export default {
    props: [ 'score' ],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = '超神了啊！'
        }else if(this.score < 400) {
            this.rank = '平平无奇'
        }else {
            this.rank = '你是乌龟吧...'
        }
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>