<template>
    <div>
      <h1>{{ title }}</h1>
      <PostForm @postAdded="addPost" />
      <PostList :posts="posts" @deletePost="deletePost" />
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  import PostForm from "@/components/PostForm.vue"; // Ajustez le chemin
  import PostList from "@/components/PostList.vue"; // Ajustez le chemin
  
  const title = 'Touïtteur';
  const posts = ref([]);
  
  const addPost = (post) => {
    const currentDate = new Date().toLocaleString();
    posts.value.push({ ...post, date: currentDate });
  };
  
  const deletePost = (index) => {
    posts.value.splice(index, 1);
  };
  </script>
  
  <style scoped>
  div {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
  }
  
  h1 {
    text-align: center;
    color: #1da1f2; /* Twitter blue */
  }
  </style>
  