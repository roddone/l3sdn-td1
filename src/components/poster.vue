<template>
    <div>
      <textarea v-model="message" placeholder="Entrez votre message"></textarea>
      <button @click="ajouterMessage">Poster</button>
      <ul>
        <li v-for="(message, index) in messages" :key="index">{{ message }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        message: '',
        messages: []
      };
    },
    methods: {
      ajouterMessage() {
        if (this.message.trim() !== '') {
          this.messages.push(this.message);
          this.message = '';
        }
      }
    }
  };
  </script>
  
  <style scoped>
  textarea {
    width: 100%;
    margin-bottom: 10px;
  }
  </style>
  