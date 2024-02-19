<template>
    <div v-for="flutter in flutters">
        <Flutter :user="flutter.user" :pub_time="flutter.pub_time" :text="flutter.text" />
    </div>
</template>

<script setup>
import Flutter from './Flutter.vue';


const props = defineProps([
    'flutters'
])
</script>