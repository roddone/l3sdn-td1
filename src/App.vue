<template>
    <div class="min-h-screen flex flex-col">
      <!-- Barre de navigation -->
      <nav class="bg-blue-500 text-white p-4 shadow-md">
        <div class="container mx-auto flex justify-between items-center">
          <h1 class="text-lg font-bold">Mon Twitter</h1>
          <div>
            <button class="bg-blue-700 hover:bg-blue-800 text-white font-bold py-2 px-4 rounded">
              Se connecter
            </button>
          </div>
        </div>
      </nav>
  
      <!-- Zone de contenu principale -->
      <div class="flex flex-1">
        <!-- Barre latérale de navigation -->
        <aside class="w-64 bg-white shadow-md">
          <ul class="space-y-2 p-4">
            <li>Accueil</li>
            <li>Explorer</li>
            <li>Notifications</li>
          </ul>
        </aside>
  
        <!-- Section principale -->
        <main class="flex-grow p-5 bg-gray-100">
          <div class="container mx-auto">
            <PostForm @add-post="addPost" />
            <PostList :posts="posts" @delete-post="deletePost" @update:posts="posts = $event" />
          </div>
        </main>
  
        <!-- Barre latérale des tendances (placeholder) -->
        <aside class="w-64 bg-white shadow-md">
          <div class="p-4">
            <h2 class="font-bold">Tendances</h2>
            <!-- Contenu placeholder -->
          </div>
        </aside>
      </div>
    </div>
  </template>
  
  <script>
  import PostForm from './components/PostForm.vue';
  import PostList from './components/PostList.vue';
  
  export default {
    name: 'App',
    components: {
      PostForm,
      PostList,
    },
    data() {
      return {
        posts: [],
      };
    },
    methods: {
      addPost(newPostContent) {
        const newPost = {
          id: Date.now(),
          content: newPostContent,
          likes: 0, // Initialisation du compteur de "J'aime"
        };
        this.posts.unshift(newPost);
        this.savePosts();
      },
      deletePost(id) {
        this.posts = this.posts.filter(post => post.id !== id);
        this.savePosts();
      },
      savePosts() {
        // Ici, vous pourriez ajouter la logique pour sauvegarder les posts, par exemple dans localStorage
      },
    },
  };
  </script>
  
  <style>
  /* Here you could add global styles or imports */
  /* Exemple de styles globaux */
body {
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

/* Styles spécifiques à l'application */
.container {
  max-width: 1280px;
}

.navbar {
  background-color: #123456; /* Exemple de couleur personnalisée */
}

  </style>  