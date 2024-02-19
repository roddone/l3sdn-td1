<template>
    <div>
      <h2>Créer une nouvelle publication</h2>
      <form @submit.prevent="createPost">
        <label for="postContent">Contenu de la publication:</label>
        <textarea v-model="newPostContent" id="postContent" required></textarea>
        <button type="submit">Publier</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newPostContent: '',
      };
    },
    methods: {
      createPost() {
        this.$emit('new-post', { content: this.newPostContent });
        // Réinitialiser le champ après la publication
        this.newPostContent = '';
      },
    },
  };
  </script>
  