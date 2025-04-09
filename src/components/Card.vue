<script setup>
import { useRouter } from "vue-router";

const router = useRouter()

const {quiz} = defineProps({
    quiz: {
        type: Object,
        required: true
    }
})

const navigareQuiz = () => {
    router.push(`/quiz/${quiz.id}`)    
}


</script>

<template>        
    <div @click="navigareQuiz" class="quiz-container">
        <div class="img-contaner">
            <img :src="quiz.img" alt="">
        </div>
        <div class="infos-container">
            <h3>{{ quiz.name }}</h3>
            <p>{{ quiz.domande.length }} Domande</p>
        </div>
    </div>

</template>


<style scoped>

.quiz-container {
  display: flex;
  flex-direction: column;
  margin-left: 40px;
  margin-right: 40px; 
  width: 200px;
  height: 280px;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 30px 21px 32px -21px rgb(0, 0, 0);
  transform-style: preserve-3d;
  transition: all 0.5s ease-in-out;
}

.quiz-container:hover {
  cursor: pointer;
  background-position: 80% 20%;
  transform: rotate3d(0.5, 1, 0, 20deg);
  box-shadow: 30px 21px 32px -21px rgb(0, 0, 0);
}

.img-contaner {
  height: 200px;
  background: white;
}

img {
  width: 200px;
  height: 200px;
  object-position: center;
  object-fit: cover;
  border-radius: 84% 16% 57% 43% / 16% 66% 34% 84%;

}

.infos-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: black;
  padding: 20px;
  background: white;
}

</style>