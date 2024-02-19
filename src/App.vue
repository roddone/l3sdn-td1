<template>
    <div id="app">
      <!-- Utilise le composant TweetForm pour la création de tweets -->
      <TweetForm @tweetPosted="addTweet" />
  
      <!-- Utilise le composant Feed pour afficher le flux de tweets -->
      <Feed :tweets="tweets" />
    </div>
  </template>
  
  <script>
  import TweetForm from './components/TweetForm.vue';
  import Feed from './components/Feed.vue';
  import { formatDistanceToNow } from 'date-fns';
  import locale from 'date-fns/locale/fr';
  
  export default {
    components: {
      TweetForm,
      Feed
    },
    data() {
      return {
        tweets: []  // Initialise une liste de tweets vide, que tu rempliras plus tard
      };
    },
    mounted() {
      // Met à jour les timestamps toutes les 60 secondes
      setInterval(() => {
        this.tweets.forEach(tweet => {
          tweet.timeAgo = this.calculateTimeAgo(new Date(tweet.createdAt));
        });
      }, 60000);
    },
    methods: {
      addTweet(tweetContent) {
        // Méthode pour ajouter un tweet à la liste
        const newTweet = {
          content: tweetContent,
          createdAt: new Date(),
          timeAgo: this.calculateTimeAgo(new Date())  // Utilise la date actuelle pour le calcul
        };
  
        this.tweets.unshift(newTweet);  // Ajoute le nouveau tweet au début de la liste
      },
      calculateTimeAgo(createdAt) {
        // Utilise la bibliothèque date-fns pour formater la date
        return formatDistanceToNow(createdAt, { addSuffix: true, locale });
      }
    }
  };
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  
  textarea {
    width: 100%;
    height: 100px;
  }
  
  button {
    margin-top: 10px;
  }
  </style>
  