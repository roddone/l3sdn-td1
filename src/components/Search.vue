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
        // Ajoutez ici la logique de recherche en fonction de searchQuery
        // Vous pouvez utiliser cette.searchQuery pour accéder à la valeur de recherche
      },
    },
  };
  </script>
  