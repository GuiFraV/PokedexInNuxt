<script setup lang="ts">
const { data: data } = await useFetch('https://pokeapi.co/api/v2/pokemon?limit=151')
</script>

<template>
     <p v-for="(pokemon, index) in data.results" :key="index">{{ index }} {{ pokemon.name }}</p>
</template>
