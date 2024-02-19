<!-- TweetDetails.vue -->
<template>
    <div>
      <h2>Détails du Tweet</h2>
      <div>
        <p>Auteur: {{ tweet.author }}</p>
        <p>Date: {{ tweet.date }}</p>
        <p>Contenu: {{ tweet.content }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      tweet: Object, 
    },
  };
  </script>
  