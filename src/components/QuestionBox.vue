<template>
  <div class="question-box-container">
    <div>
      <b-jumbotron>
        <template slot="lead">{{ currentQuestion.question }}</template>

        
        <hr class="my-4" />

        <p v-for="(answer, index) in answers" :key="index">
            {{ answer }}
        </p>

        <b-button variant="primary" href="#">Submit</b-button>
        <b-button v-if="!(totalQuestions === 9)" @click="nextQuestion" variant="success" href="#">Next</b-button>
        
      </b-jumbotron>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        currentQuestion: Object,
        nextQuestion: Function,
        totalQuestions: Number
    },
    computed: {
        answers() {
            let answers = [...this.currentQuestion.incorrect_answers, this.currentQuestion.correct_answer];
            return answers;
        } 

    }
}
</script>

