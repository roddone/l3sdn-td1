<template>
    <div id="app">
      <post-tweet @tweet-posted="addTweet" />
      <tweet-list :tweets="tweets" />
    </div>
  </template>
  
  <script>
  import TweetList from './components/TweetList.vue';
  import PostTweet from './components/PostTweet.vue';
import { useTimeAgo } from '@vueuse/core';
  
  export default {
    data() {
      return {
        tweets:
        [
        { username: 'undyingUndyne', profilePicture: '/src/assets/img/undyne.PNG', content: 'I WILL NEVER DIE', postedAt: useTimeAgo(new Date(2019, 10, 10))},
            { username: 'M3TT4T0N', profilePicture: '/src/assets/img/mettaton.png', content: 'POP QUIZZ TIME !!!!!!!', postedAt: useTimeAgo(new Date(2021, 9, 1))},
            { username: 'muffet', profilePicture: '/src/assets/img/muffet.PNG', content: 'Would you like a spider donut?', postedAt: useTimeAgo(new Date(2024, 1, 25))}
        ],
      };
    },
    methods: {
      addTweet(tweet) {
        this.tweets.push(tweet);
      },
    },
    components: {
      TweetList,
      PostTweet,
    },
  };
  </script>
  
  <style>
  #app {
    text-align: center;
    margin-top: 1em;
  }
  </style>
  