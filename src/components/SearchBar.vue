<template>
    <div>
      <input
        type="text"
        v-model="searchQuery"
        @input="filterProfiles"
        placeholder="Recherchez des profils..."
        class="search-input"
      />
      <div v-if="filteredProfiles.length" class="search-results">
        <ul>
          <li v-for="profile in filteredProfiles" :key="profile.username" @click="selectProfile(profile)">
            {{ profile.username }}
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      profiles: Array
    },
    data() {
      return {
        searchQuery: '',
        filteredProfiles: []
      };
    },
    methods: {
      filterProfiles() {
        if (this.searchQuery) {
          this.filteredProfiles = this.profiles.filter((profile) =>
            profile.username.toLowerCase().includes(this.searchQuery.toLowerCase())
          );
        } else {
          this.filteredProfiles = [];
        }
      },
      selectProfile(profile) {
        this.$emit('profile-selected', profile);
      }
    }
  };
  </script>
  
  <style scoped>
  .search-input {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #e1e8ed;
    border-radius: 5px;
  }
  
  .search-results {
    background: #fff;
    border: 1px solid #e1e8ed;
    border-radius: 5px;
  }
  
  .search-results ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  
  .search-results li {
    padding: 10px;
    border-bottom: 1px solid #e1e8ed;
    cursor: pointer;
  }
  
  .search-results li:hover {
    background-color: #f5f8fa;
  }
  
  .search-results li:last-child {
    border-bottom: none;
  }
  </style>
  