<script setup>
import { useRoute } from "vue-router"
import Question from "../components/Question.vue"
import QuestionHeader from "../components/QuestionHeader.vue"
import Result from "../components/Result.vue"
import { computed, ref } from "vue"
import quizes from "../data/quizes.json"

const route = useRoute()
const quizId = parseInt(route.params.id)

const quiz = quizes.find(it => it.id === quizId)

const currentQuestionIndex = ref(0)
const correctAnswers = ref(0)
const isCompleted = ref(false)

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const percent = computed(() => currentQuestionIndex.value / quiz.questions.length * 100)

const onOptionSelected = (isCorrect) => {
  if (isCorrect) correctAnswers.value++

  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    isCompleted.value = true
  }

  currentQuestionIndex.value++
}
</script>

<template>
  <div>
    <QuestionHeader :questionStatus="questionStatus" :percent="percent" />
    <div>
      <Question v-if="!isCompleted" :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" />
      <Result v-else :questionsLength="quiz.questions.length" :numberOfCorrectAnswers="correctAnswers" />
    </div>
  </div>
</template>
