<script setup lang="ts">


const { data: data } = await useFetch('https://pokeapi.co/api/v2/pokemon?limit=151')


</script>


<template>
     <p v-for="(pokemon, index) in data" :key="index">{{ index }} {{ pokemon }}</p>
</template>


