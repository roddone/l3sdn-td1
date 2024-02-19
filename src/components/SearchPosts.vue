<template>
    <input
        style="top: 0; left: 0; background: white; color: black; padding: 1rem; width: 100%;"
        v-model="search"
        placeholder="Rechercher dans les tweets"
    />
</template>

<script setup>
    let search = '';
</script>