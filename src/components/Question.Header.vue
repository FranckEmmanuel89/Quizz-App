<script setup>

const {questionStato, barPercentuale} = defineProps(["questionStato", "barPercentuale"])

</script>


<template>
    <header>
        <h4>{{questionStato}}</h4>
        <div class="bar">
            <div class="completion" :style="{width: barPercentuale}">

            </div>
        </div>
    </header>
</template>


<style scoped>

h4 {
    font-size: 30px;
    margin: 10px;
}

.bar {
    width: 300px;
    height: 50px;
    border: 2px solid whitesmoke;
    border-radius: 5px;
    background: whitesmoke;
}

.completion {
    height: 100%;
    width: 66%;
    background: wheat;
}

</style>