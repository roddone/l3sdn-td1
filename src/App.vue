<template>
    <Navbar/>
    
    <br>
    <Actualite/>

  </template>
  
  <script>
  import Actualite from './components/Actualite.vue';
  import Navbar from './components/Navbar.vue';
  
  export default {
    components: {
      Actualite,
      Navbar
    },
    data() {
        return {
        tweets: [] // Peut-être initialisé avec des données si nécessaire
        };
    },
    methods: {
        handleTweet(tweet) {
        this.tweets.unshift(tweet); // Ajouter le tweet en haut de la liste
        },
        handleSearch(query) {
        console.log('Recherche dans les tweets pour:', query);
        }
    }
    };
  </script>
  ./components/Actualite.vue