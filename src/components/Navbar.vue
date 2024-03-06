<template>
    <div class="navbar">
      <input type="text" v-model="searchQuery" placeholder="Rechercher dans les tweets">
      <button @click="searchTweets">Rechercher</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: ''
      };
    },
    methods: {
      searchTweets() {
        this.$emit('search', this.searchQuery);
      }
    }
  };
  </script>
  