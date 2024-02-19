<template>
    <div>
      <div class="center-container">
        <div class="post-list-container">
          <div class="post-form-container">
            <PostForm @new-post="addPost" />
          </div>
  
          <h2>Liste des publications</h2>
          <PostList :posts="combinedPosts" />
        </div>
  
        <div class="search-container">
          <Search />
        </div>
      </div>
  
      <router-view></router-view>
    </div>
  </template>
  
  <script>
  import PostForm from './components/PostForm.vue';
  import PostList from './components/PostList.vue';
  import Search from './components/Search.vue';
  
  export default {
    components: {
      PostForm,
      PostList,
      Search,
    },
    data() {
      return {
        allPosts: [],
        randomPosts: [],
        randomAuthors: ['User144', 'MonsieurPatate', 'ParisSG', 'SuperVoiture'], // Liste des utilisateurs aléatoires
      };
    },
    computed: {
      combinedPosts() {
        return [...this.allPosts, ...this.randomPosts];
      },
    },
    mounted() {
      setInterval(this.addRandomPosts, 4000);
    },
    methods: {
      addPost(newPost) {
        const formattedDate = new Date().toLocaleString();
        const postWithDetails = {
          ...newPost,
          author: 'Alban',
          date: formattedDate,
        };
  
        this.allPosts.unshift(postWithDetails);
      },
      addRandomPosts() {
        const randomPost = {
          content: `Contenu aléatoire ${Math.random()}`,
          author: this.getRandomAuthor(),
          date: new Date().toLocaleString(),
        };
        this.randomPosts.unshift(randomPost);
      },
      getRandomAuthor() {
        const randomIndex = Math.floor(Math.random() * this.randomAuthors.length);
        return this.randomAuthors[randomIndex];
      },
    },
  };
  </script>
  
  <style>
  #app {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
  }
  
  .center-container {
    width: 800px;
    display: flex;
    justify-content: space-between;
    border-left: 1px solid #ccc;
    border-right: 1px solid #ccc;
    padding: 20px;
  }
  
  .post-form-container {
    margin-bottom: 20px;
  }
  
  .post-form {
    background-color: #f5f8fa;
    border: 1px solid #e1e8ed;
    padding: 15px;
    border-radius: 8px;
  }
  
  textarea {
    width: 100%;
    padding: 8px;
    margin-top: 8px;
    border: 1px solid #ccd0d4;
    border-radius: 4px;
  }
  
  button {
    background-color: #1da1f2;
    color: #ffffff;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0d8bf1;
  }
  
  .post-list-container {
    margin-top: 20px;
  }
  
  .post-item {
    background-color: #ffffff;
    border: 1px solid #e1e8ed;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 8px;
  }
  
  .author {
    font-weight: bold;
    color: #1da1f2;
  }
  
  .date {
    color: #8899a6;
    font-size: 12px;
  }
  
  .content {
    color: #14171a;
    margin-top: 10px;
  }
  
  .search-container {
    margin-left: 20px;
    width: 200px; /* Ajustez la largeur selon vos besoins */
  }
  </style>
  