<template>
  <nav class="bg-blue-500 p-4 text-white flex justify-between items-center">
    <div class="flex items-center">
    </div>
    <div class="relative flex">
      <input v-model="searchQuery" @input="emitSearchQuery" type="text" placeholder="Rechercher des tweets" class="p-2 text-gray-700 rounded-lg">
      <span class="absolute right-10 top-3 text-gray-500 text-xs">{{ searchQuery.length }}</span>
      <button v-if="searchQuery.length" @click="clearSearch" class="absolute right-0 top-0 mt-3 mr-4 text-gray-500 hover:text-gray-700">
        &times;
      </button>
      <button @click="search" class="ml-2 px-4 py-2 bg-blue-400 text-white rounded hover:bg-blue-600">
        Chercher
      </button>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    emitSearchQuery() {
      this.$emit('search', this.searchQuery);
    },
    clearSearch() {
      this.searchQuery = '';
      this.emitSearchQuery();
    },
    search() {
      this.emitSearchQuery();
    },
  },
};
</script>
