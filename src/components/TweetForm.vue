<template>
    <form @submit.prevent="submitTweet">
      <input type="text" v-model="tweetText" placeholder="Compose your tweet...">
      <button type="submit">Tweet</button>
    </form>
  </template>
  
  <script setup>
  import { ref, defineEmits } from 'vue';
  
  const tweetText = ref('');
  
  const submitTweet = () => {
    if (tweetText.value.trim() !== '') {
      emit('tweet-created', {
        author: 'Vianney Lehu',
        content: tweetText.value,
        createdAt: new Date().toLocaleString()
      });
      tweetText.value = '';
    }
  }
  
  const emit = defineEmits(['tweet-created']);
  </script>
  