<template>
  <div id="app">
    <search-bar :profiles="profiles" @profile-selected="handleProfileSelected" />
    
    <button v-if="selectedProfile" @click="clearSelectedProfile" class="back-button">
      Retour
    </button>
    
    <tweet-input v-if="!selectedProfile" @post-tweet="handlePostTweet" />

    <!-- Affichez la liste globale de tweets quand aucun profil n'est sélectionné -->
    <tweet-list v-show="!selectedProfile" :tweets="tweets" />
    
    <!-- Affichez les tweets du profil sélectionné -->
    <tweet-list v-if="selectedProfile" :tweets="selectedProfile.tweets" />
  </div>
</template>

<script>
import TweetInput from './components/TweetInput.vue';
import TweetList from './components/TweetList.vue';
import SearchBar from './components/SearchBar.vue';

export default {
  name: 'App',
  components: {
    TweetInput,
    TweetList,
    SearchBar
  },
  data() {
    return {
      profiles: [
        {
          username: 'Fatima',
          tweets: [
            { id: 1, content: "C'est un beau jour pour coder !", date: '2023-03-05T08:00:00.000Z' },
            { id: 2, content: "Vue.js est incroyable !", date: '2023-03-05T09:00:00.000Z' }
          ]
        },
        {
          username: 'Mahmoud',
          tweets: [
            { id: 3, content: "Je suis fatigué...", date: '2023-06-07T10:00:00.000Z' },
            { id: 4, content: "Je vais me coucher.", date: '2023-08-08T11:00:00.000Z' }
          ]
        },
        {
          username: 'Said',
          tweets: [
            { id: 5, content: "Chlotsrophobie", date: '2023-10-11T10:00:00.000Z' },
            { id: 6, content: "Comment allez-vous", date: '2023-11-12T11:00:00.000Z' }
          ]
        }
      ],
      tweets: [], // Liste globale de tweets
      selectedProfile: null,
    };
  },
  methods: {
    handlePostTweet(newTweetContent) {
      const newTweet = {
        id: Date.now(),
        content: newTweetContent,
        date: new Date().toISOString()
      };
      if (this.selectedProfile) {
        this.selectedProfile.tweets.unshift(newTweet);
        this.selectedProfile = { ...this.selectedProfile };
      } else {
        this.tweets.unshift(newTweet);
      }
    },
    handleProfileSelected(profile) {
      this.selectedProfile = profile;
    },
    clearSelectedProfile() {
      this.selectedProfile = null;
    }
  }
};
</script>
  
<style scoped>
body {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  background-color: #e6ecf0;
  color: #14171a;
  line-height: 1.6;
  padding: 0;
  margin: 0;
}

#app {
  max-width: 600px;
  margin: 20px auto;
  background: #fff;
  border: 1px solid #e1e8ed;
  border-radius: 5px;
}

/* Style du composant TweetInput */
textarea {
  width: 100%;
  border: 1px solid #0970b9;
  border-radius: 5px;
  padding: 10px;
  margin: 10px 0;
  resize: none;
}

button {
  background-color: #1da1f2;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 0 10px 10px 10px;
  border-radius: 20px;
  cursor: pointer;
  font-weight: bold;
  text-transform: uppercase;
}

button:hover {
  background-color: #1991db;
}

/* Style du composant TweetList et TweetItem */
.tweet-item {
  border-bottom: 1px solid #1277c0;
  padding: 10px;
}

.tweet-item:last-child {
  border-bottom: none;
}

.tweet-content {
  font-size: 1rem;
  margin: 5px 0;
}

.tweet-time {
  font-size: 0.8rem;
  color: #657786;
}
</style>
  