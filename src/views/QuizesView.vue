<script setup>
import { ref, watch } from "vue";
import q from "../data/quiz.json";
import Card from "../components/Card.vue"

const search = ref('')

const quizes = ref(q)

watch(search, ()=> {
  quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase())) 
})


</script>

<template>
    <header>
      <h1>Quiz</h1>
      <input v-model.trim="search" type="text" name="" id="" placeholder="Search quiz...">
    </header>
    <div class="quiz-section">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
    </div>
    <footer>
      <p>Il contenuto di questo sito web è protetto da copyright ed è di proprietà di Franck Emmanuel N.D. 2025</p>
    </footer>
 
</template>

<style scoped>

.container {
  display: flex;
  align-items: center;
  flex-direction: column;
  padding: 20px;
  background-image: url(./assets/bg.jpg);
  background-size: cover;
  background-position: center;
  min-height: 100vh; 
  width: 100%;
  background-repeat: no-repeat;
  color: white;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  padding: 10px;
  margin-bottom: 80px;
  margin-top: 30px;
}

input {
  padding: 10px;
  border-radius: 5px;
  border: none;
}

.quiz-section {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 40px;
  margin-bottom: 40px;
  justify-content: center;
  max-width: 1000px;
}

footer {
  font-size: 12px;
  margin: 20px 40px;
  text-align: center;
}


</style>