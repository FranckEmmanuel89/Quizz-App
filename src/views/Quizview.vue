<script setup>
import Question from '../components/Question.vue';
import QuestionHeader from '../components/Question.Header.vue';
import Result from '../components/Result.vue';
import { useRoute } from 'vue-router';
import { computed, ref } from "vue";
import quizes from '../data/quiz.json'

const route = useRoute()
const quizId = route.params.id
const quiz = quizes.find( q=> q.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfCorrectAnswers = ref(0)
const showResults = ref(false)


const questionStato = computed(() => {
    return `${currentQuestionIndex.value}/${quiz.domande.length}`
})

const barPercentuale = computed(() => {
    return `${currentQuestionIndex.value/quiz.domande.length * 100}%`
})

const onOptionselected = (isCorrect) => {
    if(isCorrect) {
        numberOfCorrectAnswers.value++;
    }

    if(quiz.domande.length - 1 === currentQuestionIndex.value ) {
        showResults.value = true
    }
    
    currentQuestionIndex.value++
}


</script>

<template>
    <div class="container">
        <QuestionHeader :questionStato="questionStato" :barPercentuale="barPercentuale"/>
        <div class="question-container">
            <Question v-if="!showResults" :domande="quiz.domande[currentQuestionIndex]" @selectOption="onOptionselected"/>
            <Result v-else :quizQuestionLength="quiz.domande.length" :numberOfCorrectAnswers="numberOfCorrectAnswers"/>
        </div>
    </div>
</template>

<style scoped>
.container {
    max-width: 700px;
    display: flex;
}

@media (max-width: 768px) {
    .container {
        gap: 20px;
    }

}
</style>