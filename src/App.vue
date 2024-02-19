<template>
    <div id="app">
      <search-bar @search="handleSearch" />
      <tweet-box @post-tweet="handlePostTweet" />
      <tweet-list :tweets="tweets" />
    </div>
  </template>
  
  <script>
  import SearchBar from './components/SearchBar.vue';
  import TweetBox from './components/TweetBox.vue';
  import TweetList from './components/TweetList.vue';
  
  export default {
    name: 'App',
    components: {
      SearchBar,
      TweetBox,
      TweetList
    },
    data() {
      return {
        tweets: [],
        searchQuery: ''
      };
    },
    methods: {
      handleSearch(query) {
        // Mettre à jour la requête de recherche et peut-être filtrer les tweets
        this.searchQuery = query;
        console.log('Recherche en cours pour:', this.searchQuery);
        // Vous devrez ajouter une logique pour filtrer les tweets basée sur la recherche
      },
      handlePostTweet(tweetContent) {
        // Ajouter le nouveau tweet à la liste des tweets
        const newTweet = {
          id: this.tweets.length + 1,
          content: tweetContent,
          date: new Date()
        };
        this.tweets.unshift(newTweet); // Ajoute le tweet au début du tableau
      }
    }
  };
  </script>
  
  <style>
  /* Votre CSS ici */
  </style>
  