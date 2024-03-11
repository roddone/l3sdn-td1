<template>
  <div class="tweet-item">
    <p class="tweet-content">{{ tweet.content }}</p>
    <small class="tweet-time">Posté il y a {{ timeSince(tweet.date) }}</small>
  </div>
</template>

<script>
export default {
  props: {
    tweet: Object,
  },
  methods: {
    timeSince(dateString) {
      const tweetDate = new Date(dateString);
      const now = new Date();
      const secondsPast = (now.getTime() - tweetDate.getTime()) / 1000;

      if (secondsPast < 60) {
        return parseInt(secondsPast) + ' secondes';
      }

      const minutesPast = parseInt(secondsPast / 60);
      if (minutesPast < 60) {
        return minutesPast + ' minutes';
      }

      const hoursPast = parseInt(minutesPast / 60);
      if (hoursPast < 24) {
        return hoursPast + ' heures';
      }

      const daysPast = parseInt(hoursPast / 24);
      if (daysPast < 30) {
        return daysPast + ' jours';
      }

      const monthsPast = parseInt(daysPast / 30);
      if (monthsPast < 12) {
        return monthsPast + ' mois';
      }

      const yearsPast = parseInt(monthsPast / 12);
      return yearsPast + ' années';
    },
  },
};
</script>

<style scoped>
.tweet-item {
  padding: 10px;
  border-bottom: 1px solid #e1e8ed;
}

.tweet-content {
  margin: 5px 0;
}

.tweet-time {
  color: #657786;
  font-size: 0.8rem;
}
</style>
