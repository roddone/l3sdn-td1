<template>
  <div class="container">
    <div class="search-bar">
      <input
        v-model="searchQuery"
        type="text"
        class="search-input"
        placeholder="Rechercher sur Twitter"
      />
      <button class="search-button">Rechercher</button>
    </div>
    <div class="main">
      <div class="sidebar">
        <button class="sidebar-button">Home</button>
        <button class="sidebar-button">Notifications</button>
        <button class="sidebar-button">Messages</button>
      </div>
      <div class="content">
        <h1 class="title">Bienvenue sur Twitter</h1>
        <button @click="OpenTweet" class="tweet-button">Tweeter</button>
        <div v-if="showTweetModal" class="modal">
          <div class="modal-content">
            <span class="close" @click="CloseTweet">&times;</span>
            <h2>Ecrire un nouveau tweet</h2>
            <label for="username">Nom d'utilisateur:</label>
            <input type="text" id="username" v-model="newTweet.username" />
            <label for="message">Message:</label>
            <textarea id="message" v-model="newTweet.message"></textarea>
            <button @click="submitTweet">Envoyer</button>
          </div>
        </div>
        <ul class="tweet-list">
          <li v-for="element in filteredTweets" :key="element.id" class="tweet">
            <div class="user-info">
              <span class="username">{{ element.name }}</span>
              <span class="timestamp">{{ element.timestamp }}</span>
            </div>
            <div class="message">{{ element.message }}</div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const liste = ref([
  {
    id: 1,
    name: "John",
    message: "Salut, je tweete depuis Vue.js !",
    timestamp: "Envoyé à 17:21",
  },
  {
    id: 2,
    name: "Jane",
    message: "Bonjour à tous !",
    timestamp: "Envoyé à 17:22",
  },
  {
    id: 3,
    name: "Bob",
    message: "Ciao !",
    timestamp: "Envoyé à 17:23",
  },
  {
    id: 4,
    name: "Alice",
    message: "Hey !",
    timestamp: "Envoyé à 17:24",
  },
  {
    id: 5,
    name: "Charlie",
    message: "Au revoir!",
    timestamp: "Envoyé à 17:25",
  },
]);

const searchQuery = ref("");
//chercher les mots des tweet dans la barre de recherche
const filteredTweets = computed(() => {
  if (!searchQuery.value) {
    return liste.value;
  } else {
    return liste.value.filter((tweet) =>
      tweet.message.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  }
});

const showTweetModal = ref(false);

const newTweet = ref({
  username: "",
  message: "",
});

function OpenTweet() {
  showTweetModal.value = true;
}

function CloseTweet() {
  showTweetModal.value = false;
}
//écrire un nouveau tweet
function submitTweet() {
  const now = new Date();
  const timestamp = `${now.getHours()}:${now.getMinutes()}`;

  liste.value.push({
    id: liste.value.length + 1,
    name: newTweet.value.username,
    message: newTweet.value.message,
    timestamp: `Envoyé à ${timestamp}`,
  });

  CloseTweet();
}
</script>

<style scoped>
.container {
  width: 100%;
  padding: 20px;
  background-color: #f9f9f9;
}

.search-bar {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.search-input {
  width: 80%;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 10px;
}

.search-button {
  width: 15%;
  margin-left: 5%;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px;
  cursor: pointer;
}

.search-button:hover {
  background-color: #0056b3;
}

.main {
  display: flex;
}

.sidebar {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding-right: 20px;
  width: 20%;
}

.sidebar-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  margin-bottom: 10px;
  cursor: pointer;
  width: 100%;
}

.sidebar-button:hover {
  background-color: #0056b3;
}

.content {
  display: flex;
  flex-direction: column;
  width: 80%;
}

.title {
  text-align: center;
  color: #333;
}

.tweet-button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  margin-bottom: 20px;
  cursor: pointer;
}

.tweet-button:hover {
  background-color: #0056b3;
}

.tweet-list {
  list-style-type: none;
  padding: 0;
  margin-bottom: 20px;
}

.tweet {
  background-color: #fff;
  border-radius: 8px;
  padding: 15px;
}

.user-info {
  margin-bottom: 5px;
}

.username {
  font-weight: bold;
  color: #007bff;
}

.message {
  color: #333;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
}

.modal-content {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  width: 300px;
  margin-top: 200px;
}

.modal-title {
  text-align: center;
  margin-bottom: 20px;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer; /* Définir le curseur sur pointer */
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input[type="text"],
textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
}

input[type="text"]:focus,
textarea:focus {
  border-color: #007bff;
  outline: none;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.timestamp {
  color: #777;
  font-size: 12px;
  margin-left: 10px;
}
</style>
