<script setup>
import ListContainer from "./component/ListContainer.vue";
import SearchBar from "./component/SearchBar.vue";
import { ref } from "vue";

let searchVariable = ref("")
</script>

<template>
  <div class="container">
    <list-container :search="searchVariable" />
    <search-bar v-model="searchVariable"/>
    <p> {{ searchVariable }}</p>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}
</style>
