<template>
  <div>
    <div v-for="profile in profiles" :key="profile.username" class="profile">
      <h3>{{ profile.username }}</h3>
      <ul class="tweets-list">
        <li v-for="tweet in profile.tweets" :key="tweet.id" class="tweet">
          <tweet-item :tweet="tweet"></tweet-item>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import TweetItem from './TweetItem.vue';

export default {
  components: {
    TweetItem,
  },
  props: {
    profiles: Array,
  },
};
</script>
  
  <style scoped>
  .profile {
    border-bottom: 1px solid #e1e8ed;
    padding: 10px;
  }
  
  .tweets-list {
    list-style-type: none;
    padding: 0;
  }
  
  .tweet {
    margin: 5px 0;
  }
  
  .tweet-time {
    color: #657786;
    font-size: 0.8rem;
  }
  </style>
  