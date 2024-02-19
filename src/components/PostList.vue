<template>
  <ul>
    <PostItem v-for="(post, index) in posts" :key="index" :post="post" @deletePost="deletePost(index)" />
  </ul>
</template>

<script setup>
import PostItem from "./PostItem.vue";

const props = defineProps(['posts']);
const emit = defineEmits(['deletePost']);
</script>
