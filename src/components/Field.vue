<template>
    <div class="field">
      <label class="label">{{ label }}</label>
      <form class="control" @submit.prevent="addTweet">
        <input class="input" type="text" :placeholder="placeholder" v-model="value">
        <button type="submit" class="button is-primary">Tweet</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref, defineProps, defineEmits } from 'vue';
  
  defineProps(['label', 'placeholder', 'value']);
  
  const emit = defineEmits(['tweetSubmitted']);
  const value = ref('');
  
  function addTweet() {
    emit('tweetSubmitted', { profil: 'Etienne Baillieux', message: value.value, date: new Date().toLocaleString() });
    value.value = ''; 
  }
  </script>
  