<!-- components/SearchBox.vue -->
<template>
    <div class="search-box">
      <input type="text" v-model="searchQuery" placeholder="Rechercher dans les tweets">
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const searchQuery = ref('');
  </script>
  