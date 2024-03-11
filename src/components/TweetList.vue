<template>
  <div>
    <ul>
      <li v-for="tweet in tweets" :key="tweet.id" class="tweet">
        <tweet-item :tweet="tweet"></tweet-item>
      </li>
    </ul>
  </div>
</template>

<script>
import TweetItem from './TweetItem.vue';

export default {
  components: {
    TweetItem,
  },
  props: {
    tweets: Array,
  },
};
</script>

<style scoped>
.tweet {
  margin-bottom: 10px;
}
</style>