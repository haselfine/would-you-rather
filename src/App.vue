<template>
  <div id="app">
    <h1>Would you rather...</h1>
    <WouldYouRather 
      v-for = "question in questions" 
      v-bind:key="question.id"
      v-on:answer-changed = "choiceMade" 
      v-bind:question= "question.question"
      v-bind:id = "question.id"
      v-bind:answer1="question.answer1"
      v-bind:answer2="question.answer2"> <!--bind props, handle change event-->
    </WouldYouRather><br>
    <div id = "results" v-if = "filled"> <!--only display data if user selects an answer (could use v-show too)-->
      <h4>You chose:</h4>
      <ul v-for = "userChoice in userChoices" v-bind:key="userChoice.index"> <!--bind to index of array for unique value-->
        <li v-show = "userChoice"> {{userChoice}} <!--will only show answers that have been completed-->
        </li>
      </ul>
    </div>
    <div id = "results" v-else>Choose an answer above</div> <!--message if user hasn't selected an answer-->
  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data(){
    return {
      questions: [ //I chose a theme of powers
        {
          id: 0,
          question: '...be able to control fire or water?',
          answer1: 'Fire',
          answer2: 'Water'
        },
        {
          id: 1,
          question: '...be able to move silently or have an incredibly loud and scary voice?',
          answer1: 'Move silently',
          answer2: 'Loud, scary voice'
        },
        {
          id: 2,
          question: '...have super strength or super speed?',
          answer1: 'Strength',
          answer2: 'Speed'
        }
      ],
      userChoices: ['', '', ''], //initialize with 3 choices to avoid errors
      choice: '',
      filled: false //has user selected an answer yet?
    }
  },
  methods: {
    choiceMade(choiceId, choice){
      this.filled = true //user has selected an answer
      console.log(`User choice = ${choiceId, choice}`)
      this.$set(this.userChoices, choiceId, choice) //dynamically respond to user input with $set
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  margin-left: 30px;
  margin-right: 30px;
  text-anchor: middle;
  text-align: center;
}

#results{
  
  padding: 8px;
  margin: 8px;
  list-style-position: inside;
}


</style>
