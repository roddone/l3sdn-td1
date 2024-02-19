<template>
    <div class="tweet">
        <div class="profil"> {{ profil }} </div>
        <div class="message"> {{ message }} </div>
        <div class="date"> {{ date }} </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
defineProps(['profil', 'message', 'date'])
</script>