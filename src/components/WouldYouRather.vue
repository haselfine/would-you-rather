<template>
    <div class = "box">
        <h2>{{ question }}</h2>
        <input type = "radio" v-model = "choice" v-bind:value = "answer1" v-on:change = "answerChanged(choice)"> <!--send answer1 to answerChanged, parent-->
        <label>{{ answer1 }}</label><br>
        <input type = "radio" v-model = "choice" v-bind:value = "answer2" v-on:change = "answerChanged(choice)"> <!--same as above except answer2-->
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
            this.choiceId = this.id //i had trouble sending this.id so I made a variable to hold it
            console.log(this.choiceId)
            console.log(`Answer changed: ${this.choiceId, choice}`) //this isn't displaying right for some reason
            this.$emit('answer-changed', this.choiceId, choice) //send to parent
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