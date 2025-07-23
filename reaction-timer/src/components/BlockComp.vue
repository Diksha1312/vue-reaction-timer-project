<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me!
    </div>
</template>

<script lang="js">
export default {
    props: ['delay'], // Delay in milliseconds before the block appears
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(`Reaction Time: ${this.reactionTime} ms`)
        }
    }
}
</script>

<style>
.block {
    width: 400px;
    background: #42b983;
    text-align: center;
    color: white;
    padding: 100px 0;
    margin: 40px auto;
    border-radius: 20px;
}
</style>