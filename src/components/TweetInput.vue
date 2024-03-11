<template>
    <div>
      <textarea v-model="newTweet" placeholder="Quoi de neuf ?"></textarea>
      <button @click="postTweet">Tweeter</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTweet: '',
      };
    },
    methods: {
      postTweet() {
        this.$emit('post-tweet', this.newTweet);
        this.newTweet = ''; 
      },
    },
  };
  </script>
  