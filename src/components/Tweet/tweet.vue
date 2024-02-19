<script setup>
import { computed } from "vue";

const props = defineProps({
  tweet: Object,
});

const tweetDate = new Date(props.tweet.tweetDate);
const timeDifference = computed(() => {
  const diffInMilliseconds = new Date() - tweetDate;
  const diffInMinutes = Math.floor(diffInMilliseconds / 60000);
  if (diffInMinutes < 60) {
    return `${diffInMinutes} m`;
  }
  const diffInHours = Math.floor(diffInMinutes / 60);
  if (diffInHours < 24) {
    return `${diffInHours} h`;
  }
  const diffInDays = Math.floor(diffInHours / 24);
  return `${diffInDays} j`;
});
</script>

<template>
  <div class="tweet-box">
    <h3>{{ props.tweet.accountName }} (@{{ props.tweet.arobaseName }})</h3>
    <p>{{ props.tweet.tweetContent }}</p>
    <span>{{ timeDifference }}</span>
    <div class="tweet-info">
      <span>Likes: {{ props.tweet.tweetLikes }}</span>
      <span>Retweets: {{ props.tweet.tweetRetweets }}</span>
    </div>
  </div>
</template>

<style scoped>
.tweet-box {
  border: 1px solid #ccc;
  padding: 1rem;
  margin-bottom: 1rem;
  margin-top: 1rem;
  margin-left: 0.5rem;
}

.tweet-info {
  display: flex;
  justify-content: space-between;
}
</style>
