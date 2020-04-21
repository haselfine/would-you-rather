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
      v-bind:answer2="question.answer2">
    </WouldYouRather><br>
    <div id = "results" v-if = "filled">
      <h4>You chose:</h4>
      <ul v-for = "userChoice in userChoices" v-bind:key="userChoice.index">
        <li v-show = "userChoice"> {{userChoice}}
        </li>
      </ul>
    </div>
    <div id = "results" v-else>Choose an answer above</div>
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
      questions: [
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
      userChoices: ['', '', ''],
      choice: '',
      filled: false
    }
  },
  methods: {
    choiceMade(choiceId, choice){
      this.filled = true
      console.log(`User choice = ${choiceId, choice}`)
      this.$set(this.userChoices, choiceId, choice)
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
