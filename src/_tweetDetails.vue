<template>
    <div>
        <p><img :src="`https://ui-avatars.com/api/?rounded=true&name=${tweet.user}&size=32`"/> {{ tweet.user }}</p>
        <p>{{ tweet.content }}</p>
        <p>{{ timeAgo }}</p>
    </div>
</template>
<script setup>
import { computed } from 'vue'
import { useTimeAgo } from '@vueuse/core'

const props = defineProps(['tweet'])
const timeAgo = computed(() => useTimeAgo(props.tweet.date))
</script>