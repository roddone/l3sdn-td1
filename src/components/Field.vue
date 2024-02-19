<template>

    <div class="field">
        <label class="label">{{ label }}</label>
        <form class="control">
        <input class="input" type="text" :placeholder="placeholder" v-model="value">
        <button type = "submit" class="button is-primary" @click="addTweet">Tweet</button>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue'
defineProps(['label', 'placeholder', 'value'])
const placeholder = ref('Enter a value')
const value = ref('')

function addTweet() {
    tweet.value.push({profil: 'Etienne Baillieux', message: value.value, date: new Date()})
}
</script>