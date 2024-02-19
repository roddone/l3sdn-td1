<template>
    <div style="border-top: 1px solid lightgray; flex:1; padding: 1rem;">
        <img src="https://i.pravatar.cc/300" style="width: 50px;" alt="placeholder" />
        <div>
            <div>{{ toto.post.content }}</div>
            <div>@{{ toto.post.userId }}</div>
            <div>{{ formattedTime }}</div>
        </div>
    </div>
</template>

<script setup>
import { defineProps, computed, ref, watch } from 'vue';

const toto = defineProps({
    post: {
        type: Object,
        required: true,
    },
});

const time = new Date(toto.post.date);
const formattedTime = time.toLocaleString(undefined, {
    hour: 'numeric',
    minute: 'numeric',
    month: 'numeric',
    day: 'numeric',
    year: 'numeric',
});
</script>