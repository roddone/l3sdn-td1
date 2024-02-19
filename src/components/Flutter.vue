<template>
    <p>{{ user }} - {{ pub_time }}</p>
    <p>{{ text }}</p>
</template>

<script setup>

const props = defineProps([
    'user', 'pub_time', 'text'
])
</script>