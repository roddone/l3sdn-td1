<template>
  <div>
    <input v-model="content" placeholder="À quoi pensez-vous ?" />
    <button @click="postTweet">Tweet</button>
  </div>
</template>

<script>
import { useTimeAgo } from '@vueuse/core';

export default {
  data() {
    return {
      content: '',
    };
  },
  methods: {
    postTweet() {
      const tweet = {
        username: 'SansFromUndertale',
        profilePicture: "/src/assets/img/avatar.PNG",
        content: this.content,
        postedAt: useTimeAgo(new Date()),
      };

      this.$emit('tweet-posted', tweet);
      this.content = '';
    },
  },
};
</script>
