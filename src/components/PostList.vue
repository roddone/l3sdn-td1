<template>
  <div class="space-y-4">
    <div v-for="post in posts" :key="post.id" class="bg-white p-4 rounded shadow">
      {{ post.content }}
      <div class="flex justify-between items-center mt-4">
        <button @click="toggleLike(post)" class="flex items-center">
          <span class="mr-2">👍</span> J'aime ({{ post.likes }})
        </button>
        <button @click="deletePost(post.id)" class="text-red-500 hover:text-red-700">Supprimer</button>
      </div>
    </div>
  </div>
  </template>
  
  <script>
  export default {
    props: {
    posts: Array,
  },
  methods: {
    deletePost(id) {
      this.$emit('delete-post', id);
    },
    toggleLike(post) {
      post.likes += 1; // Simplement incrémenter pour l'instant
      this.$emit('update:posts', [...this.posts]);
    },
  },
  };
  </script>  
  <style>
  /* Styles pour la liste de posts */
  ul {
    list-style-type: none; /* Enlever les puces de liste */
    padding: 0;
  }
  
  li {
    background-color: white;
    margin-bottom: 8px;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1); /* Ombre douce pour chaque tweet */
    padding: 16px;
  }
  
  .delete-button {
    color: #ff0000; /* Bouton de suppression en rouge */
    float: right; /* Positionner à droite */
  }
  
  </style>
  