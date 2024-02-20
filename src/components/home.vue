<template>
    <div class="tweet-container">
      <div class="profile">
        <img :src="profilePicture" alt="Profile Picture">
        <span>{{ userName }}</span>
      </div>
      <div class="tweet-box">
        <textarea v-model="tweetContent" placeholder="What's happening?"></textarea>
        <button @click="postTweet">Tweet</button>
      </div>
      <div v-if="tweets.length > 0" class="tweet-list">
        <div v-for="tweet in tweets" :key="tweet.id" class="tweet">
          <div class="tweet-content">
            <p>{{ tweet.content }}</p>
            <div class="tweet-footer">
              <span class="time">{{ tweet.time }}</span>
              <button class="delete-button" @click="deleteTweet(tweet.id)">Delete</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        profilePicture: 'path_to_your_profile_picture', // Update this path
        userName: 'Sabine Mhanna',
        tweetContent: '',
        tweets: []
      };
    },
    methods: {
      postTweet() {
        if (this.tweetContent.trim() !== '') {
          const currentTime = new Date().toLocaleString();
          const newTweet = {
            id: Date.now(), // Changed to use Date.now() for a unique ID
            content: this.tweetContent,
            time: currentTime
          };
          this.tweets.unshift(newTweet);
          this.tweetContent = '';
        }
      },
      deleteTweet(tweetId) {
        this.tweets = this.tweets.filter(tweet => tweet.id !== tweetId);
      }
    }
  };
  </script>
  
  <style scoped>
  /* Add styles for the delete button here, along with other styles mentioned previously */
  .tweet-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .delete-button {
    background-color: #ff4d4d;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    border-radius: 15px;
  }

  .tweet-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  background-color: #fff;
  color: #14171a;
}

.profile {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.profile img {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  margin-right: 10px;
}

.tweet-box textarea {
  width: 100%;
  resize: none;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #e1e8ed;
  border-radius: 4px;
}

.tweet-box button {
  background-color: #1da1f2;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 20px;
  float: right;
}

.tweet-list {
  margin-top: 20px;
}

.tweet {
  border: 1px solid #e1e8ed;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
}

.tweet-content p {
  margin: 0 0 10px 0;
}

.time {
  color: #657786;
  font-size: 0.85em;
}
  </style>
  