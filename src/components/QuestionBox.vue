<template>
  <div class="question-box-container">
    <div>
      <b-jumbotron>
        <template slot="lead">{{ currentQuestion.question }}</template>

        
        <hr class="my-4" />

        <b-list-group>
          <b-list-group-item 
            v-for="(answer, index) in answers" 
            :key="index" 
            @click="selectAnswer(index)"
            :class="[selectedIndex === index ? 'selected' : '']">  
            
            {{ answer }}   
          </b-list-group-item>
        </b-list-group>

        <b-button variant="primary" href="#">Submit</b-button>
        <b-button v-if="!(totalQuestions === 9)" @click="nextQuestion" variant="success" href="#">Next</b-button>
        
      </b-jumbotron>
    </div>
  </div>
</template>

<script>
import _ from 'lodash'
export default {
    props: {
        currentQuestion: Object,
        nextQuestion: Function,
        totalQuestions: Number
    },
    data() {
      return {
        selectedIndex: null,
        shuffledAnswers: []
      }
    },
    computed: {
        answers() {
            let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
            return answers;
        } 
    },
    watch: {
      currentQuestion: {
        immediate: true,
        handler() {
          this.selectedIndex = null
          this.shuffleAnswers()
        }
      }
    },
    methods: {
      selectAnswer(index) {
        this.selectedIndex = index
        console.log(this.selectedIndex)
      },
      shuffleAnswers() {
        let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
        this.shuffledAnswers = _.shuffle(answers);
      }
    }
}
</script>

<style scoped>
.list-group {
  margin-bottom: 10px;
}
.btn {
  margin: 0 5px
}
.list-group-item:hover {
  background: #EEE;
  cursor: pointer;
}
.selected {
  background-color: lightblue;
}
.incorrect {
  background-color: lightcoral;
}
.incorrect {
  background-color: lightgreen;
}
</style>

