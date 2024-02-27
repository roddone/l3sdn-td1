<template>
    <div class="post-tweet-section mb-4">
      <div class="profile-picture-container">
        <img :src="profilePicture" alt="Profile Picture" class="profile-picture">
      </div>
      <textarea v-model="newTweetContent" class="form-control" rows="3" placeholder="What's happening?"></textarea>
      <button @click="postTweet" class="btn btn-primary mt-2">Tweet</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTweetContent: ''
      };
    },
    props: {
      profilePicture: String
    },
    methods: {
      postTweet() {
        if (this.newTweetContent.trim() !== '') {
        
          this.$emit('tweet-posted', this.newTweetContent);
          this.newTweetContent = '';
        }
      }
    }
  };
  </script>
  

  