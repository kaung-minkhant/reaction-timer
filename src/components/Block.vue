<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me!!
  </div>
</template>

<script>
export default {
    mounted() {
        console.log('block mounted');
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delayMS)
    },
    props: ['delayMS'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 1
            }, 1);
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
            // this.showBlock = false
        },
    },
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>