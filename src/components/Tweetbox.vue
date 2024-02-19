<template>
  <div class="p-4">
    <textarea v-model="newTweet" class="w-full p-2 text-gray-700 border rounded-lg focus:outline-none" rows="3" placeholder="Ya quoi?"></textarea>
    <button @click="postTweet" class="mt-2 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600">
      Tweet
    </button>
  </div>
</template>

<script>
export default {
  name: 'Tweetbox',
  data() {
    return {
      newTweet: '',
    };
  },
  methods: {
    postTweet() {
      if (this.newTweet.trim() !== '') {
        this.$emit('post-tweet', { content: this.newTweet, time: new Date() });
        this.newTweet = '';
      }
    },
  },
};
</script>
