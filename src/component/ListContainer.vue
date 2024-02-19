<script setup>
import Formulaire from "./Formulaire.vue";
import { ref, onMounted, computed } from "vue";

const tweetList = [
  {
    id: 1,
    username: "user1",
    content: "content1",
    date: "2020-12-01",
  },
  {
    id: 2,
    username: "user2",
    content: "content2",
    date: "2020-12-02",
  },
  {
    id: 3,
    username: "user3",
    content: "content3",
    date: "2020-12-03",
  },
];

let list = tweetList;

const props = defineProps({
  search: String,
});


const filterList = computed(() => {
  if (search !== undefined && search !== "") {
    return list.filter((tweet) => tweet.username.includes(search));
    console.log(search);
  } else {
    return list;
  }
});
</script>

<template>
  <div class="container">
    <Formulaire />
    <div v-for="Tweet in filterList" class="tweet">
      <p>De @{{ Tweet.username }}</p>
      <p>{{ Tweet.content }}</p>
      <p>{{ Tweet.date }}</p>
    </div>
  </div>
</template>

<style scoped>
.tweet {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
}

.container {
  width: 33.33%;
  display: flex;
  flex-direction: column;
}

p {
  margin: 2;
}
</style>
