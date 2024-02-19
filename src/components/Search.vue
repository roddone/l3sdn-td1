<!-- Search.vue -->
<template>
    <div>
      <input v-model="searchQuery" placeholder="Rechercher..." />
      <button @click="searchTweet">Rechercher</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
      };
    },
    methods: {
      searchTweet() {
    
      },
    },
  };
  </script>
  