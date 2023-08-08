<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HeaderView from './components/HeaderView.vue';
</script>

<template>
<HeaderView/>

<div class="form">
  <RouterView/>
</div>
  
</template>

<style scoped>
  .form{
    position: relative;
    top: 80px;
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    flex-wrap: wrap;
    flex-direction: column;
    align-content: center;
  
  }
</style>


