<template>
    <div class="search-bar">
      <input v-model="searchQuery" placeholder="Rechercher..." />
      <button @click="search">Chercher</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: ''
      };
    },
    methods: {
      search() {
        this.$emit('onSearch', this.searchQuery);
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

.search-input:focus {
  outline: none;
  box-shadow: 0 0 0 2px #1da1f2;
}

.search-button {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  background-color: #1da1f2;
  color: white;
  font-weight: bold;
  text-transform: uppercase;
}

.search-button:hover {
  background-color: #1a91da;
}

.search-button:active {
  background-color: #198ccf;
}

.search-button:focus {
  outline: none;
  box-shadow: 0 0 0 2px #1a91da;
}
</style>
  