<script setup>
import Field from './components/Field.vue';
import Tweet from './components/Tweet.vue';
import { ref } from 'vue';

const tweet = ref([]);

function handleTweetSubmitted(newTweet) {
  tweet.value.push(newTweet);
}
</script>

<template>
  <div>
    <Field label="TweetField" @tweetSubmitted="handleTweetSubmitted" />
    <Tweet v-for="tweetItem in tweet" :profil="tweetItem.profil" :message="tweetItem.message" :date="tweetItem.date" />
  </div>
</template>


<style scoped>

</style>
