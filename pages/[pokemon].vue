<script setup>
import { ref } from 'vue';
import { useRoute } from 'vue-router';

const pokemonData = ref(null); // Création d'une variable réactive pour stocker les données du Pokémon
const { pokemon } = useRoute().params;

async function fetchPokemons() {
  const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`);
  const data = await response.json();
  pokemonData.value = data; 

  console.log(data);
}


fetchPokemons();
</script>

<template>
    <div>
        <p>{{ pokemon }}</p>
        <ul v-if="pokemonData">
          <li v-for="ability in pokemonData.abilities" :key="ability.ability.name">
            Abilities : {{ ability.ability.name }}
          </li>
          <li>
            HP : {{pokemonData.stats[0].base_stat}}
          </li>
          <li>
            Attack : {{pokemonData.stats[1].base_stat}}
          </li>
          <li>
            defense : {{pokemonData.stats[2].base_stat}}
          </li>
          <li>
            special-attack : {{pokemonData.stats[3].base_stat}}
          </li>
          <li>
            special-defense : {{pokemonData.stats[4].base_stat}}
          </li>
          <li>
            speed : {{pokemonData.stats[5].base_stat}}
          </li>
          <li v-if="pokemonData.types.length > 1">
            type : {{pokemonData.types[0].type.name}}
            {{pokemonData.types[1].type.name}}
          </li>
          <li v-else>
            type : {{pokemonData.types[0].type.name}}
          </li>

        </ul>
    </div>
</template>