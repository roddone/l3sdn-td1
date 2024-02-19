<!-- components/TweetBox.vue -->
<template>
    <div class="tweet-box">
      <input type="text" v-model="username" placeholder="Nom d'utilisateur">
      <input type="text" v-model="tweetText" placeholder="Entrez votre tweet">
      <button @click="addTweet">Ajouter Tweet</button>
    </div>
  </template>
  
  <script setup>
  import { ref, defineEmits } from 'vue';
  
  const username = ref('');
  const tweetText = ref('');
  const { emit } = defineEmits(['tweet-added']);
  
  const addTweet = () => {
    if (username.value && tweetText.value) {
      emit('tweet-added', {
        username: username.value,
        text: tweetText.value,
        timestamp: Date.now()
      });
      username.value = '';
      tweetText.value = '';
    }
  };
  </script>
  