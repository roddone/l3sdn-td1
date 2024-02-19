<template>
    <div style="top: 40px; left: 0; padding: 1rem; width: 100%; display: flex; gap:30px;">
      <input v-model="postContent" @keydown.enter="addPost" style="flex: 3; padding: 1rem;" placeholder="Votre tweet ici" />
      <button @click="addPost" style="flex: 1; padding: 1rem; color:white; border-radius: 30px; background: rgb(17, 195, 255); outline: 0; border: 0; cursor:pointer;">Nouveau tweet.</button>
    </div>
  </template>

  <script setup>
  import { ref, defineProps, defineEmits } from 'vue';

  const { posts, search } = defineProps(['posts', 'search']);
  const emit = defineEmits();

  const postContent = ref('');

  const addPost = () => {
    if (postContent.value.trim() !== '') {
      emit('add-post', postContent.value);
      postContent.value = '';
    }
  };
  </script>
