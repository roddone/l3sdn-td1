<!-- App.vue -->
<template>
    <div id="app">
      <h1>Faux Twitter</h1>
      
      <!-- Champs de tweet -->
      <TweetBox @tweet-added="addTweet" />
  
      <!-- Champ de recherche -->
      <SearchBox v-model="searchQuery" />
  
      <!-- Liste des tweets -->
      <TweetList :tweets="tweets" :searchQuery="searchQuery" />
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import TweetBox from './components/TweetBox.vue';
  import SearchBox from './components/SearchBox.vue';
  import TweetList from './components/TweetList.vue';
  
  const username = ref('');
  const tweetText = ref('');
  const tweets = ref([]);
  const searchQuery = ref('');
  
  const addTweet = (tweet) => {
    tweets.value.unshift(tweet);
  };
  
  const generateRandomTweets = () => {
    const examples = [
      { username: 'Alice', text: 'Premier tweet aléatoire.', timestamp: Date.now() - 10000 },
      { username: 'Bob', text: 'Deuxième tweet aléatoire.', timestamp: Date.now() - 20000 },
      { username: 'Charlie', text: 'Troisième tweet aléatoire.', timestamp: Date.now() - 30000 }
    ];
    tweets.value = examples;
  };
  
  onMounted(() => {
    generateRandomTweets();
  });
  </script>
  