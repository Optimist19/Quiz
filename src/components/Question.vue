<template>
  	<div class="question-container">
 		<h1 class="question">{{question.text}}</h1>
  	</div>
	<div class="options-container">
		<div class="option" v-for="option in question.options" :key="option.id" @click="emiSelectedOption(option.isCorrect)">
			<p class="option-label">{{option.label}}</p>
			<div class="option-value">
				<p>{{option.text}}</p>
			</div>
		</div>
  	</div>
</template>

<script setup>
import {defineProps, defineEmits} from "vue"

const emit = defineEmits(["selectOption"])

const {question} = defineProps(['question'])

const emiSelectedOption = (isCorrect) =>{
	emit("selectOption", isCorrect)
}

</script>

<style scoped>

.question-container{
	margin-top: 20px;
}

.question{
	margin-bottom: 20px;
	font-size: 40px;
}

.option{
	display: flex;
	margin-bottom: 20px;
	cursor: pointer;
}

.option-label{
	background-color: bisque;
	height: 50px;
	width: 50px;
	display: flex;
	font-size: 30px;
	align-items: center;
	justify-content: center;
}

.option-value{
	width: 100%;
	font-size: 30px;
	padding: 0 20px;
	background-color: rgb(244, 239,239);
}
</style>
