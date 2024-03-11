<template>
    <div>
      <div v-for="profile in profiles" :key="profile.username" class="profile">
        <h3>{{ profile.username }}</h3>
        <ul class="tweets-list">
          <li v-for="tweet in profile.tweets" :key="tweet.id" class="tweet">
            {{ tweet.content }}
            <small class="tweet-time">Posté {{ timeSince(tweet.date) }}</small>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
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
                { id: 3, content: "Chlotsrophobie", date: '2023-10-11T10:00:00.000Z' },
                { id: 4, content: "Comment allez-vous", date: '2023-11-12T11:00:00.000Z' }
                ]
         }
        ]
      };
    },
    methods: {
      timeSince(dateString) {
      },
    }
  };
  </script>
  
  <style scoped>
  .profile {
    border-bottom: 1px solid #e1e8ed;
    padding: 10px;
  }
  
  .tweets-list {
    list-style-type: none;
    padding: 0;
  }
  
  .tweet {
    margin: 5px 0;
  }
  
  .tweet-time {
    color: #657786;
    font-size: 0.8rem;
  }
  </style>
  