<template>
    <div class = "box">
        <h2>{{ question }}</h2>
        <input type = "radio" v-model = "choice" v-bind:value = "answer1" v-on:change = "answerChanged(choice)">
        <label>{{ answer1 }}</label><br>
        <input type = "radio" v-model = "choice" v-bind:value = "answer2" v-on:change = "answerChanged(choice)">
        <label>{{ answer2 }}</label>
    </div>
</template>

<script>
export default {
    name: 'WouldYouRather',
    data(){
        return {
            choice: '',
            choiceId: Number
        }
    },
    methods: {
        answerChanged(choice){
            console.log(this.id)
            this.choiceId = this.id
            console.log(this.choiceId)
            console.log(`Answer changed: ${this.choiceId, choice}`)
            this.$emit('answer-changed', this.choiceId, choice)
        }
    },
    props: {        
        question: String,
        answer1: String,
        answer2: String,
        id: Number
    }
}
</script>


<style>
    div.box{
        background-color: purple;
        color: white;
        margin: 8px;
    }
</style>