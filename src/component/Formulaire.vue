<script setup>
import { ref } from "vue";

let tweet = defineModel({
  username: String,
  content: String,
  date: String,
});

const content = ref("");
const username = ref("user1");

const handleForm = () => {
  const tweetForm = {
    username: username.value,
    content: content.value,
    date: Date.now(),
  };
  
  tweet.value = tweetForm;
  
  content.value = "";
};
</script>

<template>
  <form class="tweet">
    <div>
      <input
        v-model="content"
        type="text"
        id="content"
        name="content"
        placeholder="Partagez votre avis..."
      />
    </div>
    <div class="button">
      <div @click="handleForm">Publier</div>
    </div>
  </form>
</template>

<style scoped>
.tweet {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.button {
  margin-top: 10px;
  border: none;
}

#content {
  width: 100%;
  padding: 10px;
  margin: 10px;
  border: 1px solid #ccc;
}
</style>
