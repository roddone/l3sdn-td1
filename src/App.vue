<template>
    <div id="app">
      <Sidebar />
      <div class="main-content">
        <ProfileSection :profile-picture="profilePicture" @profile-picture-updated="updateProfilePicture" />
        <PostTweetSection :profile-picture="profilePicture" @tweet-posted="addNewTweet" />
        <TweetFeed :tweets="tweets" @tweet-deleted="deleteTweet" />
        <TrendingTopics />
        <SuggestedAccounts />
      </div>
    </div>
  </template>
  
  <script>
  import Sidebar from './components/Sidebar.vue';
  import ProfileSection from './components/ProfileSection.vue';
  import PostTweetSection from './components/PostTweetSection.vue';
  import TweetFeed from './components/TweetFeed.vue';
  import TrendingTopics from './components/TrendingTopics.vue';
  import SuggestedAccounts from './components/SuggestedAccounts.vue';
  
  export default {
    components: {
      Sidebar,
      ProfileSection,
      PostTweetSection,
      TweetFeed,
      TrendingTopics,
      SuggestedAccounts
    },
    data() {
      return {
        profilePicture: '', 
        tweets: [
          { id: 1, author: 'User1', content: 'This is a tweet about something interesting.' },
          { id: 2, author: 'You', content: 'Your own tweet that you can delete.' }
        
        ]
      };
    },
    methods: {
      updateProfilePicture(profilePicture) {
        this.profilePicture = profilePicture;
      },
      addNewTweet(content) {
        this.tweets.unshift({ id: this.tweets.length + 1, author: 'You', content });
      },
      deleteTweet(tweetId) {
        this.tweets = this.tweets.filter(tweet => tweet.id !== tweetId);
      }
    }
  };
  </script>
  
  <style>
 
  #app {
    display: flex;
  }
  
  .main-content {
    flex-grow: 1;
    padding: 20px;
  }
  
  .profile-section {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .profile-info {
    display: flex;
    align-items: center;
  }
  
  .profile-details {
    margin-left: 20px;
  }
  
  .profile-picture {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  
  .post-tweet-section {
    display: flex;
    align-items: flex-start;
    margin-bottom: 20px;
  }
  
  .profile-picture-container {
    margin-right: 20px;
  }
  
  .profile-picture-container img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  
  textarea {
    width: calc(100% - 70px); 
    min-height: 50px; 
    resize: none;
    margin-bottom: 10px;
  }
  
  .btn-primary {
    margin-top: 5px;
  }
  
  .tweet-feed {
    margin-bottom: 20px;
  }
  
  .tweet-card {
    background-color: #000000;
    border: 1px solid #000000;
    border-radius: 5px;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  .trending-topics,
  .suggested-accounts {
    margin-bottom: 20px;
  }
  

  </style>
  