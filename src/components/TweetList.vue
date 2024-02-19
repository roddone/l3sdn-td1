<!-- components/TweetList.vue -->
<template>
    <div class="tweets">
      <Tweet v-for="(tweet, index) in filteredTweets" :key="index" :tweet="tweet" />
    </div>
  </template>
  
  <script setup>
  import { computed } from 'vue';
  import Tweet from './Tweet.vue';
  
  const props = defineProps({
    tweets: Array,
    searchQuery: String
  });
  
  const filteredTweets = computed(() => {
    if (!props.searchQuery) {
      return props.tweets;
    } else {
      const query = props.searchQuery.toLowerCase();
      return props.tweets.filter(tweet => tweet.text.toLowerCase().includes(query));
    }
  });
  </script>
  