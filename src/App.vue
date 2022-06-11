<template>
  <div class="ctr">
    <QuizQuestions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    />
    <QuizResult
      v-else
      :totalCorrect="totalCorrect"
      :questionsAnswered="questionsAnswered"
    />
    <button type="button" class="reset-btn" @click.prevent="resetQuiz">
      Reset
    </button>
  </div>
</template>

<script>
import QuizQuestions from "./components/QuizQuestions.vue";
import QuizResult from "./components/QuizResult.vue";
export default {
  name: "App",
  components: {
    QuizQuestions,
    QuizResult,
  },

  methods: {
    questionAnswered(is_correct) {
      this.questionsAnswered++;
      if (is_correct) {
        this.totalCorrect++;
      }
    },
    resetQuiz() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
  data() {
    return {
      totalCorrect: 0,
      questionsAnswered: 0,
      questions: [
        {
          q: "What is 2 + 2?",
          answers: [
            {
              text: "4",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: "5",
              is_correct: false,
            },
            {
              text: "7",
              is_correct: false,
            },
            {
              text: "6",
              is_correct: true,
            },
            {
              text: "12",
              is_correct: false,
            },
          ],
        },
        {
          q: "Find the missing letter: C_ke",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "a",
              is_correct: true,
            },
            {
              text: "i",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
