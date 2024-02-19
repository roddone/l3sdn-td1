<template>
<nav class="center">
    <ul>
      <li @click="selectedTab = 'For You'" :class="{ 'active': selectedTab === 'For You' }">For You</li>
      <li @click="selectedTab = 'Following'" :class="{ 'active': selectedTab === 'Following' }">Following</li>
      <li @click="selectedTab = 'Search'" :class="{ 'active': selectedTab === 'Search' }">Search</li>
    </ul>
  </nav>
</template>

<script setup>
    import { ref } from 'vue';

    const selectedTab = ref('For You');
</script>

<style scope>
    nav {
  background-color: #f0f0f0;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
}

li {
  padding: 10px 20px;
  cursor: pointer;
}

li:hover {
  background-color: #ddd;
}

.active {
  background-color: #ccc;
}
</style>