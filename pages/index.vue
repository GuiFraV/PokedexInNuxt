<script setup lang="ts">
import { onMounted, ref } from 'vue';

const pokemons = ref([]);

async function fetchPokemons() {
  const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=151');
  const data = await response.json();
  const promises = data.results.map(async (pokemon) => {
    const response = await fetch(pokemon.url);
    return await response.json();
  });
  pokemons.value = await Promise.all(promises);
}

onMounted(fetchPokemons);
</script>

<template>
  <div v-for="(pokemon, index) in pokemons" :key="index">
    <h2>{{ pokemon.name }}</h2>
    <img :src="pokemon.sprites.front_default" alt="pokemon.name" />
    <p>Type: <span v-for="(type, index) in pokemon.types" :key="index">{{ type.type.name }}</span></p>
  </div>
</template>
