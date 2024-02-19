<script setup>

let search = defineModel();

</script>

<template>
   <div>
        <input
        v-model="search"
        type="text"
        id="search"
        name="search"
        placeholder="Rechercher un utilisateur..."
        />
   </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
}
</style>
