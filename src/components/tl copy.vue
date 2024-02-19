<script setup>
  import { ref } from "vue";
  
  const title = 'Twitter';
  const tl = ref([]);
  
  const add = () => {
    tl.value.push({ value: valeurInput.value, action: 'Add' });
    valeurInput.value = '';
  };
</script>
  
<template>
    <div>
        <div>
            <h1>{{ title }}</h1>
        </div>
    
        <input type="text" v-model="valeurInput" placeholder="What is happening ?">
        <button @click="add">Post</button>
  
        <ul>
            <li v-for="(item, index) in tl" :key="index">{{ item.value }}</li>
        </ul>
    </div>
</template>
  
<style>
    button {
    background: blue;
    color: white;
    padding: 5px 15px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    }
    button:hover {
    background: darkblue;
    transition: all 0.3s ease-in-out;
    }
</style>
  