<script setup>
import { RouterView } from "vue-router";

</script>

<template>
  <div class="container">
    <RouterView />
  </div>
 </template>

<style scoped>

.container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background-image: url(./assets/bg.jpg);
  background-size: cover;
  background-position: center;
  min-height: 100vh; 
  width: 100%;
  background-repeat: no-repeat;
  color: white;
}

</style>
