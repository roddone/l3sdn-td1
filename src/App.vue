<template>
  <div id="app">
    <search-bar @onSearch="handleSearch" />
    <tweet-box @post-tweet="handlePostTweet" />
    <tweet-list :tweets="tweets" />
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import TweetBox from './components/TweetBox.vue';
import TweetList from './components/TweetList.vue';

export default {
  components: {
    SearchBar,
    TweetBox,
    TweetList
  },
  data() {
    return {
      tweets: []
    };
  },
  methods: {
    handleSearch(searchQuery) {
      // Implémentez la logique de recherche ici...
    },
    handlePostTweet(newTweet) {
      const newTweetObject = {
        id: this.tweets.length + 1,
        content: newTweet,
        date: new Date().toISOString() // Stockez la date en format ISO pour la compatibilité
      };
      this.tweets.unshift(newTweetObject); // Ajoutez le nouveau tweet au début du tableau
    }
  }
};
</script>
  
  <style>
  </style>
  