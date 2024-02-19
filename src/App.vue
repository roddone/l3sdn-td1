<template>

    <ul style="list-style-type: none; margin: 0; padding: 0;">
        <div style="text-align: center; margin-top: 20px;">
      <input type="text"
             style="width: 300px; height: 40px; margin-bottom: 20px;"
             v-model="textInput"
             @keyup.enter="addTweet"
             placeholder="Écrivez quelque chose et appuyez sur Entrée">
    </div>
      <li v-for="(tweet, index) in tweets" :key="index">
        <Tweet :tweet="tweet" />
      </li>
    </ul>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import Tweet from './Tweet.vue'
  const textInput = ref('');
  const tweets = ref([]);
  
  function addTweet() {
    if (textInput.value.trim() !== '') {
      const now = new Date();
      const dateTimeString = now.toLocaleString();
  
      tweets.value.unshift({ text: textInput.value, dateTime: dateTimeString });
      textInput.value = '';
    }
  }
  </script>
  
  <style scoped>
  
  </style>
  