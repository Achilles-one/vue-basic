<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me!
  </div>
</template>

<script>
export default {
    props: [ 'deplay' ],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        // console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            // console.log(this.deplay)
            this.startTimer()
        }, this.deplay)
    },
    // updated() {
    //     console.log('component updated')
    // },
    // unmounted() {
    //     console.log('unmounted')
    // },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            // console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>