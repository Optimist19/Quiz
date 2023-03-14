<template>
    <!-- <router-link :to="`/question/${quiz.id}`" class="card"> -->
    <!-- <router-link :to="{name: 'CardQuest', params:{id:quiz.id}}" class="card"> -->

	<!-- Any of the above can serve as routing. So we used div instead of router link, and then created a function and call it in the div tag. We want to do programmatical routing-->

    <div @click="clickDiv" class="card">
      <img :src="quiz.img" alt="A book picture of a subject" />
      <div class="card-text">
        <h2>{{ quiz.name }}</h2>
        <!-- <h2>Math</h2> -->
        <p>{{ quiz.questions.length }} questions</p>
      </div>
    </div>
</template>

<script setup>
import { useRouter } from "vue-router";
import { defineProps } from "vue";

const router = useRouter();

const { quiz } = defineProps(["quiz"]);
console.log(quiz);

const clickDiv = () => {
  router.push(`/quiz/${quiz.id}`);
};
</script>

<style>
.card {
  width: 310px;
  overflow: hidden;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  border-radius: 2%;
}

.card img {
  width: 100%;
  height: 190px;
  margin: 0;
}

.card .card-text {
  padding: 0 5px;
}

.card .card-text h2 {
  font-weight: bold;
}
</style>
