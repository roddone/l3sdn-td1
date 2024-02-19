<template>
  <div class="flex flex-col space-y-2">
    <tweet-box @post-tweet="addTweet"></tweet-box>
    <div v-for="(tweet, index) in filteredTweets" :key="index" class="p-4 max-w-sm mx-auto bg-white rounded-xl shadow-md space-y-2">
      <div class="font-bold">{{ tweet.author }}</div>
      <div class="text-gray-500 text-base">
        {{ tweet.content }}
      </div>
      <div class="text-gray-400 text-sm">
        {{ timeSince(tweet.time) }}
      </div>
    </div>
  </div>
</template>

<script>
import TweetBox from './Tweetbox.vue';

export default {
  name: 'Feed',
  components: {
    TweetBox,
  },
  props: ['searchQuery'],
  data() {
    return {
      tweets: [
        { author: 'Tourtel Twist', content: 'Sans alcool la fête est pas folle', time: new Date(2024, 0, 1, 9, 30) },
        { author: 'ElMav59', content: 'J\'adore perdre à fc 24', time: new Date(2023, 0, 2, 14, 15) }
      ],
    };
  },
  computed: {
    filteredTweets() {
      if (!this.searchQuery) {
        return this.tweets;
      }
      return this.tweets.filter(tweet => {
        return tweet.content.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
               tweet.author.toLowerCase().includes(this.searchQuery.toLowerCase());
      });
    },
  },
  methods: {
    addTweet(newTweet) {
      this.tweets.unshift({
        author: 'Théo le Big Boss',
        content: newTweet.content,
        time: new Date(),
      });
    },
    timeSince(date) {
      const seconds = Math.floor((new Date() - date) / 1000);
      let interval = Math.floor(seconds / 60);
      if (interval < 60) {
        return interval + " minutes ago";
      }
      interval = Math.floor(interval / 60);
      if (interval < 24) {
        return interval + " hours ago";
      }
      interval = Math.floor(interval / 24);
      return interval + " days ago";
    },
  },
  mounted() {
    this.interval = setInterval(() => {
      this.tweets = this.tweets.map(tweet => ({
        ...tweet,
        time: new Date(tweet.time)
      }));
    }, 60000);
  },
  beforeDestroy() {
    clearInterval(this.interval);
  },
};
</script>
