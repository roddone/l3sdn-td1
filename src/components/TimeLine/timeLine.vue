<script setup>
import TweetBox from "../Tweet/tweet.vue";
import { defineProps, ref } from "vue";
const props = defineProps({
  tweets: Array,
  postTweet: Function,
});

const newTweet = ref("");

const post = () => {
  if (newTweet.value === "") {
    return;
  }
  props.postTweet();
  newTweet.value = "";
};
</script>

<template>
  <div>
    <div>
      <input
        type="text"
        id="search"
        name="search"
        placeholder="Quoi de neuf?"
        class="textArea"
        v-model="newTweet"
      />
      <button class="postButton" @click="post">Publier</button>
    </div>
    <div class="timeline">
      <TweetBox v-for="(tweet, index) in tweets" :key="index" :tweet="tweet" />
    </div>
  </div>
</template>

<style scoped>
.textArea {
  width: 100%;
  height: 70px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  margin-top: 10px;
}
.postButton {
  margin-left: 0.5rem;
  width: 100%;
  height: 40px;
  border: none;
  border-radius: 5px;
  background-color: #00b7ff;
  color: white;
  font-weight: bold;
  margin-top: 10px;
}
</style>
