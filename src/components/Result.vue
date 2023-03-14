<template>
  <div class="results">
	<p>Your Results...</p>
	<h1>
		{{numberOfCorrectAnswers}}/
		{{quizQuestionsLength}}
	</h1>
	<router-link to="/">Back to home</router-link>
  </div>
</template>

<script setup>
import {defineProps} from "vue"

const {numberOfCorrectAnswers, quizQuestionsLength} = defineProps(["numberOfCorrectAnswers","quizQuestionsLength"])
</script>

<style scoped>
.results{
	text-align: center;
	padding: 100px 0;
}


p{
	font-size: 25px;
}

h1{
	font-size: 80px;
}
</style>