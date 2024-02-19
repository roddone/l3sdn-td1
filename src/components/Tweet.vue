<!-- components/Tweet.vue -->
<template>
    <div class="tweet">
      <div class="tweet-box">
        <div class="tweet-header">
          <span class="username">{{ tweet.username }}</span>
          <span class="time">{{ getTimeSinceTweet(tweet.timestamp) }}</span>
        </div>
        <div class="tweet-text">{{ tweet.text }}</div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const props = defineProps({
    tweet: Object
  });
  
  const getTimeSinceTweet = (timestamp) => {
    const now = Date.now();
    const seconds = Math.floor((now - timestamp) / 1000);
  
    if (seconds < 60) {
      return `${seconds} secondes`;
    } else if (seconds < 3600) {
      const minutes = Math.floor(seconds / 60);
      return `${minutes} minutes`;
    } else if (seconds < 86400) {
      const hours = Math.floor(seconds / 3600);
      return `${hours} heures`;
    } else {
      const days = Math.floor(seconds / 86400);
      return `${days} jours`;
    }
  };
  </script>
  