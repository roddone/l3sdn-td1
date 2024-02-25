<template>
    <label>Recherche : </label><input v-model="search" />
</template>

<script setup>
const search = defineModel()
</script>