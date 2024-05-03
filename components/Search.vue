<script setup>

const pokemonId = ref(0);

async function submit(){

    const response = await fetch( `https://pokeapi.co/api/v2/pokemon/${pokemonId.value}` )
    const data = await response.json();
    console.log(data);
}


</script>

<template>

    <form @submit.prevent action="/card">
        <input v-model="pokemonId" type="text" placeholder="Search..">
        <button @click="submit()">Search</button>
    </form>

</template>