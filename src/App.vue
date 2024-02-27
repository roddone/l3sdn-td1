<template>
  <div class="app-container">
    <h1 class="title">FrancescoTwi Tweets</h1>
    <div class="add-tweet-container">
      <textarea v-model="newTweetContent" placeholder="What's happening?" class="tweet-input"></textarea>
      <button @click="publishTweet" class="publish-button">Publish</button>
    </div>
    <div class="search-bar-container">
      <input v-model="searchQuery" placeholder="Search tweets" class="search-input" />
    </div>
    <div v-for="tweet in filteredTweets" :key="tweet.id" class="tweet">
      <div class="tweet-content">{{ tweet.content }}</div>
      <div class="tweet-created">Posted: {{ tweet.created }}</div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      newTweetContent: '', // This will hold the new tweet text
      searchQuery: '' ,
      tweets: [] // This will hold the list of tweets
    };
  },
  computed: {
    // Update the computed property to filter tweets
    filteredTweets() {
      if (!this.searchQuery) {
        return this.tweets;
      }
      return this.tweets.filter(tweet =>
        tweet.content.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    }
  },
  methods: {
    publishTweet() {
      if (!this.newTweetContent) return; // Prevent publishing if the field is empty
      
      const newTweet = {
        id: Date.now(),
        content: this.newTweetContent,
        created: new Date().toLocaleString(),
      };
      
      this.tweets.push(newTweet);
      this.newTweetContent = ''; // Reset textarea after publishing
      this.updateLocalStorage(); // Update localStorage with the new tweet
    },
    updateLocalStorage() {
      localStorage.setItem('tweets', JSON.stringify(this.tweets));
    },
    loadTweets() {
      const tweets = localStorage.getItem('tweets');
      if (tweets) {
        this.tweets = JSON.parse(tweets);
      }
    }
  },
  created() {
    this.loadTweets(); // Load tweets from localStorage when the component is created
  }
};
</script>


<style scoped>
.app-container {
  width: 100%;
  margin: 0 auto;
  padding: 20px;
  border: none;
  background-color: #fff;
  }

html, body {
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
  background-color: #fff;
}


.title {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.add-account-container {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.account-input {
  flex: 1;
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.add-button {
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.add-button:hover {
  background-color: #0056b3;
}

.account {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  padding: 10px;
  background-color: white;
  border: 1px solid #e1e4e8;
  border-radius: 5px;
}
.add-tweet-container {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.tweet-input {
  flex: 1;
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  height: 100px; /* Larger area for tweet content */
  resize: vertical; /* Allow vertical resize only */
}

.publish-button {
  padding: 10px 20px;
  background-color: #1da1f2; /* Twitter's brand color for the button */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.publish-button:hover {
  background-color: #0d95e8;
}
.account-photo {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  margin-right: 15px;
}

.account-info {
  flex: 1;
}

.account-name {
  font-size: 16px;
  font-weight: bold;
  color: #333;
}

.account-created {
  font-size: 14px;
  color: #666;
}

.search-bar-container {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.search-input {
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 100%; /* Full width of the container */
}

.tweet {
  background-color: #f8f9fa;
  border: 1px solid #e1e4e8;
  border-radius: 5px;
  padding: 10px;
  margin-bottom: 10px;
}

.tweet-content {
  font-size: 16px;
  color: #333;
}

.tweet-created {
  font-size: 14px;
  color: #666;
  margin-top: 8px;
}
</style>
