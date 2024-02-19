<script setup>
let searching = defineModel();
</script>

<template>
  <div>
    <div>
      <input
        type="text"
        id="searchBar"
        name="searchBar"
        placeholder="Chercher?"
        class="searchBar"
        v-model="searching"
      />
    </div>
  </div>
</template>

<style scoped>
.searchBar {
  width: 100%;
  height: 1rem;
  border: 1px solid #ccc;
  border-radius: 1rem;
  padding: 1rem;
  margin-top: 1rem;
  margin-left: 3rem;
}
</style>
