<template>
    <div>
      <form @submit.prevent="submitTweet">
        <textarea v-model="tweetContent" placeholder="Quoi de neuf ?"></textarea>
        <button type="submit">Poster</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        tweetContent: ''
      };
    },
    methods: {
      submitTweet() {
        if (this.tweetContent.trim() !== '') {
          this.$emit('tweetPosted', this.tweetContent);
  
          this.tweetContent = '';
        }
      }
    }
  };
  </script>
  