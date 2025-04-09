<script setup>

const emit = defineEmits(["selectOption"])

const emitselectedOption = (isCorrect) => {
    emit("selectOption", isCorrect)
}

const {domande} = defineProps({
    domande: {
        type: Object,
        required: true
    }
})



</script>



<template>
    <div class="domanda-container">
        <p class="domanda">{{domande.text}}</p>
    </div>
    <div class="scelte-riposte-contanier">
        <div @click="emitselectedOption(opzione.isCorrect)" v-for="opzione in domande.opzioni" :key="opzione.id" class="scelta">
            <p class="scelta-option">{{ opzione.label }}</p>
            <div class="scelta-valore">
                <p>{{ opzione.text }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>

.scelte-riposte-contanier {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;  
}

.domanda-container {
    color: black;
    margin: 40px 20px;
    background: rgb(253, 249, 244);
    height: 150px;
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

.domanda-container p {
    font-weight: 600;
    padding: 10px 20px;
}

.domanda {
    margin-bottom: 20px;
    font-size: 30px;
}

.scelta {
   display: flex;
   gap: 10px;
   margin-bottom: 20px;
   cursor: pointer;
}

.scelta-option {
    color: black;
    width: 50px;
    border-radius: 50%;
    height: 50px;
    font-size: 20px;
    background: wheat;
    display: flex;
    align-items: center;
    justify-content: center;
}

.scelta-valore {
    color: black;
    background: whitesmoke;
    font-size: 24px;
    width: 680px;
    display: flex;
    align-items: center;
    padding: 10px 20px;
    border-radius: 5px;
}

.scelta-valore:hover {
    background: rgb(248, 210, 138);
}
@media (max-width: 768px) {
    .scelta-valore {
        width: 500px;
        font-size: 20px 
    }
    .scelta-option {
        width: 50px;
        height: 50px;
        font-size: 18px;
    }
    .domanda-container {
        width: 550px;
        padding-top: 20px;
        padding-bottom: 20px;
    }
    .domanda {
        font-size: 24px;
    }
}

@media (max-width: 599px) {
    .scelta-valore {
        width: 400px;
        font-size: 20px 
    }
    .scelta-option {
        width: 50px;
        height: 50px;
        font-size: 18px;
    }
    .domanda-container {
        width: 450px;
        padding-top: 20px;
        padding-bottom: 20px;
    }
    .domanda {
        font-size: 22px;
    }
}

@media (max-width: 480px) {
    .scelta-valore {
        width: 300px;
        font-size: 15px
    }

    .scelta-option {
        width: 40px;
        height: 40px;
        font-size: 14px;
    }

    .domanda {
        font-size: 20px;
    }
    .domanda-container {
        width: 350px;
    }

}

</style>