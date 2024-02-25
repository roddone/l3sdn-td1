<template>
    <textarea placeholder="What's up ?" v-model="tweetContent" @keydown.enter.ctrl="postTweet" />
    <button @click="postTweet">Poster !</button>
</template>

<script setup>
import { ref } from 'vue'
const tweetContent = ref('')
const emits = defineEmits(['postTweet'])

const postTweet = () => {
    emits('postTweet', tweetContent.value)
    tweetContent.value = ''
};
</script>