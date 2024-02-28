<template>
  <div>
    <tweet-item v-for="tweet in tweets" :tweet="tweet" />
  </div>
</template>

<script>
import TweetItem from './TweetItem.vue';

export default {
  props: {
    tweets: {
      type: Array,
      required: true,
    },
  },
  components: {
    TweetItem,
  },
};
</script>
