<template>
  <div style="border-top: 1px solid lightgray; flex:1; padding: 1rem;">
    <img src="https://i.pravatar.cc/300" style="width: 50px;" alt="placeholder" />
    <div>
      <div>{{ toto.post.content }}</div>
      <div>@{{ toto.post.userId }}</div>
      <div>{{ diff }}</div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, computed, ref, watch } from 'vue';
const now = ref(new Date());

const toto = defineProps({
  post: {
    type: Object,
    required: true,
  },
});

const diff = computed(() => {
  if (!toto.post.date) return '';
  const postDate = new Date(toto.post.date);
  const diff = now.value - postDate;
  const seconds = Math.floor(diff / 1000);
  const minutes = Math.floor(seconds / 60);
  const hours = Math.floor(minutes / 60);
  const days = Math.floor(hours / 24);
  if (days > 0) return `${days} jours`;
  if (hours > 0) return `${hours} heures`;
  if (minutes > 0) return `${minutes} minutes`;
  return `${seconds} secondes`;
});
watch(now, () => {
  diff.value;
});

setInterval(() => {
  now.value = new Date();
}, 1000);
</script>
