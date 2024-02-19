<script setup>
import like from './components/like.vue'
import poster from './components/poster.vue'
import search from './components/search.vue'
import { ref } from 'vue'

const clickcout = ref(0);

</script>

<template>

<div><poster/></div> 
<br/>
<div><search/></div>

<br>

<div>
    <like title="jaime" v-model="clickcout" />
    <p>NBjaimes : {{ clickcout }}</p>

</div>





</template>


<style scoped>
</style>