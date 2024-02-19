<template>
  <div>
    <label for="username">Username:</label>
    <input type="text" v-model="username" placeholder="Your username">
    <label for="post">What is happening?</label>
    <input type="text" v-model="postText" placeholder="Write your post">
    <button @click="addPost">Post</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits(['postAdded']);
const username = ref('');
const postText = ref('');

const addPost = () => {
  if (username.value && postText.value) {
    emit('postAdded', { username: username.value, postText: postText.value });
    username.value = '';
    postText.value = '';
  }
};
</script>
