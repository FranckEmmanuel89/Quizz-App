<script setup>
import { RouterLink } from "vue-router";

const {quizQuestionLength, numberOfCorrectAnswers} = defineProps(["quizQuestionLength", "numberOfCorrectAnswers"])

const esitoMeg = () => {
    if (numberOfCorrectAnswers < 10) {
        return "Molto male. Devi ripetere l'anno. Mi dispiace 😢"
    } else if(numberOfCorrectAnswers >= 10 && numberOfCorrectAnswers < 15){
        return "Non ci siamo ancora. Continua a studiare 🫡"
    } else if(numberOfCorrectAnswers >= 15 && numberOfCorrectAnswers < 19) {
        return "Ci sei quasi. Ancora un piccolo sforzo 👍"
    } else if (numberOfCorrectAnswers >= 19 && numberOfCorrectAnswers < 26){
        return "Complimenti hai passato l'anno 🥳"
    } else {
        return "Bravissimooo era una passeggiata per te ✨🎉"
    }
}
</script>



<template>

    <div class="results">
       <p>Il Tuo Punteggio...</p>
       <h4>
            {{ numberOfCorrectAnswers }}/{{ quizQuestionLength }}
        </h4>
        <span class="esito">{{ esitoMeg() }}</span>
        <RouterLink class="router-link" to="/">Torna Indietro</RouterLink>
    </div>


</template>

<style scoped>

.esito {
    margin-bottom: 20px;
}

.router-link {
    text-decoration: none;
    background: white;
    padding: 10px 5px;
    border-radius: 20px;
    border: 2px solid rgb(212, 210, 210);
    transition: background-color 0.5s ease-in-out;
}

.router-link:hover {
    text-decoration: none;
    background-color: wheat;
}

.router-link-active {
  color: inherit;
  text-decoration: none;
}

.results {
    background: whitesmoke;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    gap: 20px;
    color: black;
    text-align: center;
    padding: 50px 50px;
    margin-top: 50px;
    border: 5px solid rgb(239, 201, 130);
}

p {
    font-size: 25px;
    font-weight: bold;
}

h4 {
    font-size: 50px;
}

@media (max-width: 480px) {
    .results {
        margin: 30px 20px;
    }
}


</style>