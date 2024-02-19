<template>
    <div class="tweet-box">
      <textarea v-model="newTweet" placeholder="Quoi de neuf ?" class="tweet-textarea"></textarea>
      <button @click="postTweet" class="tweet-button">Poster</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTweet: ''
      };
    },
    methods: {
      postTweet() {
        if (this.newTweet) {
          this.$emit('onPost', this.newTweet);
          this.newTweet = ''; // Réinitialiser le champ de saisie
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .tweet-box {
    display: flex;
    flex-direction: column;
    margin: 1rem;
  }
  
  .tweet-textarea {
    resize: none;
    padding: 1rem;
    margin-bottom: 0.5rem;
    border: 1px solid #e1e8ed;
    border-radius: 10px;
    min-height: 100px;
    font-size: 1rem;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  }
  
  .tweet-textarea:focus {
    border-color: #1da1f2;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1), 0 0 0 2px #1da1f2;
    outline: none;
  }
  
  .tweet-button {
    padding: 0.5rem 2rem;
    border: none;
    border-radius: 20px;
    cursor: pointer;
    background-color: #1da1f2;
    color: white;
    font-weight: bold;
    text-transform: uppercase;
    align-self: flex-end;
  }
  
  .tweet-button:hover {
    background-color: #1a91da;
  }
  
  .tweet-button:active {
    background-color: #198ccf;
  }
  
  .tweet-button:focus {
    outline: none;
    box-shadow: 0 0 0 2px #1a91da;
  }
  </style>
  