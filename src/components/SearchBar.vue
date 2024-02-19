<template>
  <div class="search-bar">
    <input
      type="text"
      v-model="searchQuery"
      @input="filterResults"
      @keyup.enter="confirmSelection"
      placeholder="Rechercher..."
      class="search-input"
    />
    <div class="search-results" v-show="searchQuery && (filteredAccounts.length || filteredTweets.length)">
      <ul>
        <li v-for="account in filteredAccounts" :key="account.id" @click="selectResult(account)">
          {{ account.name }} - {{ account.passion }}
        </li>
        <li v-for="tweet in filteredTweets" :key="tweet.id" @click="selectResult(tweet)">
          {{ tweet.content }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      accounts: [
        { id: 1, name: 'Abdi' , passion: 'Manga'},
        { id: 2, name: 'Bertrand', passion: 'Sport' },
        { id: 3, name: 'Charles', passion: 'Cinéma' },
        { id: 4, name: 'Dounia', passion: 'Trading' },
        { id: 5, name: 'Eric', passion: 'Dessin Animés' },
        { id: 6, name: 'Florian', passion: 'Voitures' },
        { id: 7, name: 'Guedid', passion: 'Motos' },
        { id: 8, name: 'Hannah', passion: 'Marque de vêtements' },
        { id: 9, name: 'Ismael', passion: 'Manga' },
        { id: 10, name: 'Junior', passion: 'Sport' },
        { id: 11, name: 'Karima',passion: 'Tennis' },
        { id: 12, name: 'Louanne', passion: 'Manga' }
      ],
      tweets: [ /* ... vos tweets ... */ ],
      filteredAccounts: [],
      filteredTweets: [],
      selectedResult: null,
    };
  },
  methods: {
    filterResults() {
      this.filterAccounts();
      this.filterTweets();
    },
    filterAccounts() {
      if (!this.searchQuery) {
        this.filteredAccounts = [];
        return;
      }
      this.filteredAccounts = this.accounts.filter(account =>
        account.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
    filterTweets() {
      if (!this.searchQuery) {
        this.filteredTweets = [];
        return;
      }
      this.filteredTweets = this.tweets.filter(tweet =>
        tweet.content.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
    selectResult(result) {
      this.selectedResult = result;
      this.searchQuery = '';
      this.filteredAccounts = [];
      this.filteredTweets = [];
    },
    confirmSelection() {
      if (this.filteredAccounts.length || this.filteredTweets.length) {
        this.selectResult(this.filteredAccounts.length ? this.filteredAccounts[0] : this.filteredTweets[0]);
      }
    }
  }
};
</script>

<style scoped>
.search-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 1rem;
  padding: 0.5rem;
  background-color: #f8f8f8;
  border-radius: 20px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
}
.search-input {
  flex-grow: 1;
  border: none;
  padding: 0.5rem 1rem;
  margin-right: 0.5rem;
  border-radius: 20px;
  font-size: 1rem;
}

.search-results {
  position: absolute;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 4px;
  width: 100%;
  z-index: 1000;
}
.search-results ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.search-results li {
  padding: 10px;
  cursor: pointer;
}
.search-results li:hover {
  background-color: #f9f9f9;
}
</style>
