<template>
    <div class="tweet">
      <div class="author">{{ tweet.author }}</div>
      <div class="content">{{ tweet.content }}</div>
      <div class="createdAt">{{ tweet.createdAt }}</div>
    </div>
  </template>
  
  <script setup props="tweet">
  </script>
  
  <style scoped>
  .tweet {
    margin-bottom: 20px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .author {
    font-weight: bold;
  }
  
  .createdAt {
    color: #888;
  }
  </style>
  