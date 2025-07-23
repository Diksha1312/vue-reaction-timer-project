<template>
    <div>
        <p>Reaction Time - {{ score }} ms.</p>
        <p class="rank"> Your rank is: {{ rank }}</p>
  </div>
</template>

<script>
export default {
    props: ['score'], // Score to display
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 400) {
            this.rank = 'Excellent';
        } else if (this.score < 600) {
            this.rank = 'Good';
        } else if (this.score < 800) {
            this.rank = 'Average';
        } else {
            this.rank = 'Poor';
        }   
    }
}
</script>

<style>
    .rank {
        font-weight: bold;
        color: #42b983;
    }
</style>