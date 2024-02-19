<template>
     <div class="mb-4 p-4 bg-white rounded shadow">
    <form @submit.prevent="submitPost" class="space-y-2">
      <textarea v-model="newPost" placeholder="Quoi de neuf ?" class="border p-2 w-full rounded" :class="{ 'border-red-500': newPost.length > 280 }"></textarea>
      <div class="flex justify-between items-center">
        <div>{{ newPost.length }}/280</div>
        <button type="submit" class="bg-blue-400 hover:bg-blue-500 text-white font-bold py-2 px-4 rounded" :disabled="newPost.length > 280 || newPost.length === 0">
          Tweeter
        </button>
      </div>
    </form>
  </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newPost: '',
      };
    },
    methods: {
      submitPost() {
        if (this.newPost.trim()) {
          this.$emit('add-post', this.newPost);
          this.newPost = '';
        }
      },
    },
  };
  </script>  
  <style>
  /* Styles pour le formulaire de post */
  form {
    background-color: #f9f9f9; /* Légère couleur de fond */
    border-radius: 8px;
    padding: 16px;
  }
  
  textarea {
    border: 2px solid #e2e8f0; /* Couleur de bordure plus claire */
    border-radius: 8px;
  }
  
  button {
    background-color: #1da1f2; /* Couleur spécifique du bouton, similaire à Twitter */
    color: white;
    border-radius: 20px;
    padding: 8px 16px;
    font-weight: bold;
    cursor: pointer;
  }
  
  button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  </style>
  