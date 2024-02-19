<template>
    <div class="twitter-input">
        <input type="text" v-model="valeurInput" placeholder="Quoi de neuf ?">
      <button @click="add">Post</button>
    </div>
</template>
  
<script setup>
  import { defineEmits } from 'vue';
    import { ref } from 'vue';
    let valeurInput = ref('');
  const emit = defineEmits();
  function add() {
    console.log('working');
    emit('add-input', valeurInput);
  }
</script>

<style>
  .twitter-input button {
    padding: 10px 20px;
    background-color: #1da1f2;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  .twitter-input {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .twitter-input input {
    flex: 1;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    margin-right: 10px;
  }

  .twitter-input button:hover {
    background-color: #0c84c3;
  }
</style>