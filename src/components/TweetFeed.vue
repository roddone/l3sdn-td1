<template>
    <div class="tweet-feed mb-4">
      <h2>Feed</h2>
      <div v-for="tweet in tweets" :key="tweet.id" class="tweet-card card mb-2">
        <div class="card-body">
          <h5 class="card-title">{{ tweet.author }}</h5>
          <p class="card-text">{{ tweet.content }}</p>
          <button v-if="tweet.author === 'You'" @click="deleteTweet(tweet.id)" class="btn btn-danger">Delete</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      tweets: Array
    },
    methods: {
      deleteTweet(tweetId) {
   
        this.$emit('tweet-deleted', tweetId);
      }
    }
  };
  </script>
