<template>
    <p>Reaction time: {{ score }} milliseconds</p>
    <h1 class="rank">{{ rank }}</h1>
</template>

<script>
export default {
    props: {
        score: Number,
    },
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = 'Ninja fingers...🥷🏻'
        } else if (this.score < 400) {
            this.rank = 'Rapid reflexes...🔥'
        } else if(this.score < 1500) {
            this.rank = 'Snail pace...🐌'
        } else {
            this.rank = 'Sloth...👀'
        }
    }
}
</script>

<style>
.rank {
    color: #0faf87;
}
</style>