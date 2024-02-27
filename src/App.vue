<template>
  <div id="app">
    <Tweet />
  </div>
</template>

<script>
import Tweet from './components/home.vue';

export default {
  name: 'App',
  components: {
    Tweet
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
}
</style>
