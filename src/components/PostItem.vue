<template>
  <li>
    <strong>{{ post.username }}</strong> - {{ post.postText }} - {{ post.date }}
    <button @click="deletePost">Delete</button>
  </li>
</template>

<script setup>
const props = defineProps(['post']);

const deletePost = () => {
  emit('deletePost');
};
</script>
