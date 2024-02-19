<template>
  <div class="tweet-list">
    <div v-for="tweet in tweets" :key="tweet.id" class="tweet-item">
      <p>{{ tweet.content }}</p>
      <small>Posté il y a {{ timeSince(tweet.date) }}</small>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tweets: Array
  },
  methods: {
    timeSince(date) {
      const seconds = Math.floor((new Date() - new Date(date)) / 1000);
      let interval = Math.floor(seconds / 31536000);

      if (interval >= 1) {
        return interval + " an" + (interval > 1 ? "s" : "");
      }
      interval = Math.floor(seconds / 2592000);
      if (interval >= 1) {
        return interval + " mois";
      }
      interval = Math.floor(seconds / 86400);
      if (interval >= 1) {
        return interval + " jour" + (interval > 1 ? "s" : "");
      }
      interval = Math.floor(seconds / 3600);
      if (interval >= 1) {
        return interval + " heure" + (interval > 1 ? "s" : "");
      }
      interval = Math.floor(seconds / 60);
      if (interval >= 1) {
        return interval + " minute" + (interval > 1 ? "s" : "");
      }
      return Math.floor(seconds) + " seconde" + (seconds > 1 ? "s" : "");
    }
  }
};
</script>
  
  <style scoped>
  .tweet-list {
    margin: 1rem;
  }
  
  .tweet-item {
    border-bottom: 1px solid #e1e8ed;
    padding: 1rem 0;
  }
  
  .tweet-item:last-child {
    border-bottom: none;
  }
  
  .tweet-item p {
    margin: 0 0 0.5rem 0;
    color: #14171a;
    font-weight: 400;
  }
  
  .tweet-item small {
    color: #657786;
    font-size: 0.875rem;
  }
  </style>