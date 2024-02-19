
<template>
    <div class="tweet">
      <p>{{ tweet.text }}</p>
      <small>{{ tweet.dateTime }}</small>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue'
  
  const props = defineProps({
    tweet: Object
  })
  </script>
  
  <style scoped>
  .tweet {
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 4px;
  }
  
  small {
    color: #666;
  }
  </style>
  