<script setup>
import { computed, ref, onMounted } from "vue";
import NavBar from "./components/NavBar/navBar.vue";
import TimeLine from "./components/TimeLine/timeLine.vue";
import SearchBar from "./components/SearchBar/searchBar.vue";

let searching = ref("");

const tweets = ref([]);

const tweetsToDisplay = computed(() => {
  if (searching.value === "") {
    return tweets.value;
  } else {
    return tweets.value.filter((tweet) =>
      tweet.tweetContent.toLowerCase().includes(searching.value.toLowerCase())
    );
  }
});

const fetchTweets = async () => {
  const response = await fetch("./tweets.json");
  if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
  }
  tweets.value = await response.json();
};

const postTweet = async () => {
  const tweetContent = document.getElementById("search").value;
  const tweet = {
    accountName: "John Doe",
    arobaseName: "johndoe",
    tweetContent: tweetContent,
    tweetDate: new Date(),
    tweetLikes: 0,
    tweetRetweets: 0,
  };
  tweets.value = [tweet, ...tweets.value];
};

onMounted(async () => {
  await fetchTweets();
});
</script>

<template>
  <div class="container">
    <NavBar />
    <TimeLine :tweets="tweetsToDisplay" :postTweet="postTweet" />
    <SearchBar v-model="searching" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  width: 100%;
  justify-content: center;
  gap: 2rem;
}
</style>
