<template>
    <div>
      <h1>Twitter</h1>
      <Navbar @search="handleSearch" />
      <div>
        <h2>Actualités</h2>
        <div v-if="filteredTweets.length > 0">
          <div v-for="tweet in filteredTweets" :key="tweet.id">
            <h3>{{ tweet.author }}</h3>
            <p>{{ formatDateTime(tweet.date) }}</p>
            <p>{{ tweet.content }}</p>
          </div>
        </div>
      </div>
      <textarea v-model="newTweet" placeholder="Quoi de neuf ?"></textarea>
      <button @click="postTweet">Tweeter</button>
    </div>
  </template>
  
  <script>
  import Navbar from './components/Navbar.vue';
  import Actualite from './components/Actualite.vue';

  
  export default {
    props: {
      tweets: Array
    },
    components: {
      Navbar
    },
    data() {
      return {
        newTweet: '',
        searchQuery: ''
      };
    },
    computed: {
      filteredTweets() {
        return this.tweets.filter(tweet => {
          return tweet.content.toLowerCase().includes(this.searchQuery.toLowerCase());
        });
      }
    },
    methods: {
      postTweet() {
        if (this.newTweet.trim() !== '') {
          this.$emit('tweeted', {
            id: this.tweets.length + 1,
            author: 'Anonymous',
            date: new Date().toISOString(),
            content: this.newTweet.trim()
          });
          this.newTweet = '';
        }
      },
      formatDateTime(dateTime) {
        const options = { year: 'numeric', month: 'short', day: 'numeric', hour: '2-digit', minute: '2-digit' };
        return new Date(dateTime).toLocaleDateString('en-US', options);
      },
      handleSearch(query) {
        this.searchQuery = query;
      }
    }
  };
  </script>