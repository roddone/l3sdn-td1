<template>
  <div class="app-container">
    <h1 class="title">FrancescoTwi Tweets</h1>
  <div v-if="!username" class="username-input-container">
    <input v-model="usernameInput" placeholder="What's your name?" class="username-input" />
    <button @click="saveUsername" class="username-save-button">Save</button>
  </div>

    <div v-else class="add-tweet-container">
      <textarea v-model="newTweetContent" placeholder="What's happening?" class="tweet-input"></textarea>
      <button @click="publishTweet" class="publish-button">Tweet</button>
    </div>
    <div class="search-bar-container">
      <input v-model="searchQuery" placeholder="Search tweets" class="search-input" />
    </div>
    <div v-for="tweet in filteredTweets" :key="tweet.id" class="tweet">
      <div class="tweet-header">
        <img :src="generateProfilePicURL(tweet.username)" alt="profile" class="profile-pic" />
        <span class="tweet-username">{{ tweet.username }}</span>
        <span class="tweet-created">{{ tweet.created }}</span>
      </div>
      <div class="tweet-content">{{ tweet.content }}</div>
      <div class="tweet-actions">
        <button @click="likeTweet(tweet)" class="like-button">
          ❤️ {{ tweet.likes }}
        </button>
        <button @click="removeTweet(tweet.id)" class="remove-tweet-button">Remove Tweet</button>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      usernameInput: '',
      username: '',
      newTweetContent: '',
      searchQuery: '',
      tweets: []
    };
  },
  computed: {
  filteredTweets() {
    return this.searchQuery
      ? this.tweets.filter(tweet =>
          tweet.content.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
          tweet.username.toLowerCase().includes(this.searchQuery.toLowerCase())
        )
      : this.tweets;
  }
},
  methods: {
    generateProfilePicURL(username) {
    return `https://via.placeholder.com/50?text=${username.substring(0, 1).toUpperCase()}`;
  },
    removeTweet(tweetId) {
    if (confirm('Are you sure you want to remove this tweet?')) {
      this.tweets = this.tweets.filter(tweet => tweet.id !== tweetId);
      this.updateLocalStorage();
    }
  },

    saveUsername() {
      if (!this.usernameInput) {
        alert('Please enter your name.');
        return;
      }
      this.username = this.usernameInput;
      localStorage.setItem('username', this.username);
    },
    publishTweet() {
      if (!this.newTweetContent) return;

      if (!this.username) {
    alert('Please enter your name.');
    return;
    }

      const newTweet = {
        id: Date.now(),
        username: this.username,
        content: this.newTweetContent,
        created: new Date().toLocaleString(),
        likes: 0
      };

      this.tweets.unshift(newTweet);
      this.newTweetContent = '';
      this.username = '';
      localStorage.removeItem('username');
      this.updateLocalStorage();
    },
    likeTweet(tweet) {
      tweet.likes++;
      this.updateLocalStorage();
    },
    updateLocalStorage() {
      localStorage.setItem('tweets', JSON.stringify(this.tweets));
    },
    loadTweets() {
      const tweets = localStorage.getItem('tweets');
      if (tweets) {
        this.tweets = JSON.parse(tweets);
      }
    },
    loadUsername() {
      const savedUsername = localStorage.getItem('username');
      if (savedUsername) {
        this.username = savedUsername;
      }
    }
    
  },
  created() {
    this.loadTweets();
    this.loadUsername(); 
  }
};

</script>

<style scoped>
.username-input-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.username-input {
  width: 70%;
  padding: 15px;
  margin-right: 10px;
  box-sizing: border-box;
  border: 2px solid #1da1f2;
  border-radius: 20px;
  font-size: 16px;
  outline: none;
}

.username-save-button {
  padding: 15px 30px;
  background-color: #1da1f2;
  color: white;
  border: none;
  border-radius: 20px;
  font-size: 16px;
  cursor: pointer;
  outline: none;
  transition: background-color 0.3s ease; 
}

.username-save-button:hover {
  background-color: #0d8bcd;
}

.tweet-input {
  width: calc(100% - 22px);
  box-sizing: border-box;
  padding: 10px;
  margin-bottom: 10px;
}

.publish-button {
  width: calc(100% - 22px);
  padding: 10px;
  background-color: #1da1f2;
  color: white;
  border: none;
  cursor: pointer;
  box-sizing: border-box;
}

.tweet-username, .tweet-created, .tweet-content {
  color: black;
}


.app-container {
  width: 100%;
  margin: 0 auto;
  padding: 20px;
  border: none;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

html, body {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  background-color: #e6ecf0;
}

.title {
  color: #1da1f2;
}

.add-tweet-container {
  border-bottom: 2px solid #e6ecf0;
  margin-bottom: 20px;
}

.tweet-input {
  border: 1px solid #e6ecf0;
}

.publish-button {
  background-color: #1da1f2;
}

.search-input {
  width: 33%;
  padding: 5px;
  display: block;
  border: 2px solid #1da1f2;
  border-radius: 2px;
  font-size: 15px;
}


.tweet {
  background-color: #fff;
  border: 1px solid #e1e4e8;
  border-radius: 10px;
  margin-bottom: 10px;
}

.tweet-header {
  display: flex;
  align-items: center;
  margin-bottom: 5px;
}

.profile-pic {
  border-radius: 50%;
  margin-right: 10px;
}

.tweet-username {
  font-weight: bold;
  color: #1da1f2;
  margin-right: 10px;
}

.tweet-actions {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.like-button {
  background: none;
  border: none;
  color: #e0245e;
  cursor: pointer;
  font-size: 16px;
}

.like-button:hover {
  opacity: 0.7;
}

.remove-tweet-button {
  padding: 5px 10px;
  background-color: #ff4757;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-left: 10px;
}

.remove-tweet-button:hover {
  background-color: #e84118;
}

</style>
