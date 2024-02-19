<template>
  <div class="min-h-screen bg-gray-100">
    <nav-bar @search="handleSearch"></nav-bar>
    <div class="flex">
      <side-bar class="hidden md:block"></side-bar>
      <feed :search-query="searchQuery" class="flex-grow"></feed>
    </div>
  </div>
</template>

<script>
import NavBar from './components/Navbar.vue';
import SideBar from './components/Sidebar.vue';
import Feed from './components/Feed.vue';

export default {
  name: 'App',
  components: {
    NavBar,
    SideBar,
    Feed,
  },
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    handleSearch(query) {
      this.searchQuery = query;
    },
  },
};
</script>
