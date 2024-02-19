<template>
    <div>
      <TweetForm @tweet-created="addTweet"></TweetForm>
      <div v-for="(tweet, index) in tweets" :key="index">
        <div v-if="tweet">
          <!-- Render tweet content -->
          <div>{{ tweet.author }}</div>
          <div>{{ tweet.content }}</div>
          <div>{{ tweet.createdAt }}</div>
        </div>
        <div v-else>
          <!-- Handle case when tweet prop is undefined or null -->
          <div>No tweet data available</div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import Tweet from './components/Tweet.vue';  
  import TweetForm from './components/TweetForm.vue';
  const tweets = ref([]);
  
  const addTweet = (newTweet) => {
    tweets.value.unshift(newTweet);
  };
  </script>
    