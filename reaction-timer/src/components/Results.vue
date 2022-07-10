<template>
  <h3 class="scoreclass">Your reaction time was {{ score }} milliseconds</h3>
  <h2 class="rankclass">{{ rank }}</h2>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if (this.score<300) {
                this.rank = "Dayumm....Awesome reflexes";
            }
        else if (this.score>300 && this.score<500) {
                this.rank = "That's the reflex I'm talkin' about.... Aim for Awesome Reflex";
            }
        else {
                this.rank = "You're slow asf dude :(";
            }
        console.log("missed this oops");
    },
    methods: {}
}
</script>

<style>
    .rankclass {
        color: green;
    }
    .scoreclass {
        position:relative;
        margin-left: 650px;
        padding: 20px auto;
        border-radius: 10px;
        border: 2px solid green;
        width: 600px;
        height: 25px;
    }
</style>