<template>
    <form @submit.prevent="submitTweet">
      <input type="text" v-model="tweet.name" placeholder="Votre nom" />
      <textarea v-model="tweet.message" placeholder="Quoi de neuf ?"></textarea>
      <button type="submit">Tweeter</button>
    </form>
  </template>

<script setup>
import { ref } from 'vue';
import { defineEmits } from 'vue';


// Définition des événements que ce composant peut émettre
const emit = defineEmits(['add-tweet']);

const tweet = ref({
  name: '',
  message: '',
  date: ''
});

const submitTweet = () => {
  tweet.value.date = new Date(); // On garde l'objet Date pour le traitement
  emit('add-tweet', { ...tweet.value }); 
  // Réinitialiser le formulaire après l'envoi
  tweet.value.name = '';
  tweet.value.message = '';
};


</script>

<style>

</style>