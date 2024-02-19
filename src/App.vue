<script setup>
import Field from './components/Field.vue';
import Tweet from './components/Tweet.vue';

import { ref } from 'vue';
const tweet = ref ({});
</script>

<template>
    <Field label="Name" />
    <Tweet v-for="tweet in tweet" :profil="tweet.profil" :message="tweet.message" :date="tweet.date" />





</template>

<style scoped>
</style>
