<template>
    <div>
      <Tweet v-for="tweet in tweets" :key="tweet.id" :tweetContent="tweet.content" :timeAgo="tweet.timeAgo" />
    </div>
  </template>
  
  <script>
  import Tweet from './Tweet.vue';
  
  export default {
    components: {
      Tweet
    },
    props: ['tweets']
  };
  </script>
  