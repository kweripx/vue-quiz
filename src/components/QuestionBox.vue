<template>
  <div class="question-container">
    <b-jumbotron>
      <template #lead>
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4">

      <p v-for="(answer, index) in answers" :key="index">
        {{ answer }}
      </p>

      <b-button variant="primary" href="#" class="mr-2">Submit</b-button>
      <b-button @click="next" variant="success" href="#">
        Next
      </b-button>
    </b-jumbotron>
  </div>
</template>

<script>
  export default {
    props: {
      currentQuestion: Object,
      next: Function
    },
    computed: {
      answers() {
       let answers = [...this.currentQuestion.incorrect_answers]
       answers.push(this.currentQuestion.correct_answers)
       return answers
      }
    },
    mounted() {
      console.log(this.currentQuestion)
    }
  }
</script>
