<template>
  <div>
    <ul>
      <li v-for="tweet in tweets" :key="tweet.id">
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
  