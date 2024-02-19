<template>
  <ul>
    <li v-for="post in filteredPosts" :key="post.date" style="flex: 1; padding: .5rem;">
      <Tweet :post="post" />
    </li>
  </ul>
</template>

<script setup>
import { computed, defineProps } from 'vue';
import Tweet from './Tweet.vue';
const props = defineProps(['posts', 'search']);
const filteredPosts = computed(() =>
  props.posts
    .filter(post =>
      post.content.toLowerCase().includes(props.search.toLowerCase())
    )
    .sort((a, b) => new Date(b.date) - new Date(a.date))
);
</script>
