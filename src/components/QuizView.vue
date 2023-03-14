<template>
  <div>
	<!-- {{quizId}} -->
	<!-- {{	{{barPercentage}} }}-->
	<QuizHeader :questionStatus="questionStatus" :barPercentage = "barPercentage"/>
	<div>
		<Question :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" v-if="!showResults"/>
		<!-- {{numberOfCorrectAnswers}}
		<button @click="currentQuestionIndex++">Next Question</button> -->
		<Results v-else :numberOfCorrectAnswers = "numberOfCorrectAnswers" 
		:quizQuestionsLength = "quiz.questions.length"/>
	</div>
  </div>
</template>

<script setup>
import Question from "./Question.vue"
import QuizHeader from "./QuizHeader.vue"
import quizes from "../data.json"
import {useRoute} from "vue-router"
import {ref, computed} from "vue"
import Results from "./Result"

// components:{
// 	Results
// }
const showResults = ref(false)
const route = useRoute()

const quizId = parseInt(route.params.id)

const quiz = quizes.find(q => q.id === quizId)

const currentQuestionIndex = ref(0)

const numberOfCorrectAnswers = ref(0)

const onOptionSelected = (isCorrect) =>{
	if(isCorrect){
		numberOfCorrectAnswers.value++
	}

	if(quiz.questions.length - 1 === 		currentQuestionIndex.value){
		showResults.value = true
	}
	currentQuestionIndex.value++
}

// const questionStatus = ref(`${currentQuestionIndex.value} / ${quiz.questions.length}`)

// watch(() => currentQuestionIndex.value, () =>{
// 	questionStatus.value = `${currentQuestionIndex.value} / ${quiz.questions.length}`
// })

// const questionStatus = computed(() => {
// 	return `${currentQuestionIndex.value}/${quiz.questions.length}`})


const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)

const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)

// export default {
// 	name: "CardQuest",
// 	components:{
// 		Question,
// 		QuizHeader
// 	}
// }
</script>

<style scoped>

</style>