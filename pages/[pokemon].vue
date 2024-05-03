<script setup>
  import {
    ref
  } from 'vue';
  import {
    useRoute
  } from 'vue-router';

  const pokemonData = ref(null); // Création d'une variable réactive pour stocker les données du Pokémon
  const {
    pokemon
  } = useRoute().params;

  async function fetchPokemons() {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`);
    const data = await response.json();
    pokemonData.value = data;

    console.log(data);
  }


  fetchPokemons();
</script>

<template>
  <div class="center">
    <div class="grid">

      <div>
        <span class="icon">
          <img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/58.png">
        </span>
        <h2>{{ pokemon }}</h2>
        <div v-if="pokemonData">
          <h3 v-if="pokemonData.types.length > 1">
            Type : {{pokemonData.types[0].type.name}}
            {{pokemonData.types[1].type.name}}
          </h3>
          <h3 v-else>
            Type : {{pokemonData.types[0].type.name}}
          </h3>

        </div>
        <p>
          Abilities :
        </p>
      </div>
      <div>
        <h2>characteristic</h2>
        <ul v-if="pokemonData">
          <li v-for="ability in pokemonData.abilities" :key="ability.ability.name">
            Abilities : {{ ability.ability.name }}
          </li>
          <li>
            HP : {{pokemonData.stats[0].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[0].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[0].base_stat > 25 & pokemonData.stats[0].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[0].base_stat >= 50 & pokemonData.stats[0].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[0].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
          </li>
          <li>
            Attack : {{pokemonData.stats[1].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[1].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[1].base_stat > 25 & pokemonData.stats[1].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[1].base_stat >= 50 & pokemonData.stats[1].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[1].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
          </li>
          <li>
            defense : {{pokemonData.stats[2].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[2].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[2].base_stat > 25 & pokemonData.stats[2].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[2].base_stat >= 50 & pokemonData.stats[2].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[2].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
          </li>
          <li>
            special-attack : {{pokemonData.stats[3].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[3].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[3].base_stat > 25 & pokemonData.stats[3].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[3].base_stat >= 50 & pokemonData.stats[3].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[3].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
          </li>
          <li>
            special-defense : {{pokemonData.stats[4].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[4].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[4].base_stat > 25 & pokemonData.stats[4].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[4].base_stat >= 50 & pokemonData.stats[4].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[4].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
          </li>
          <li>
            speed : {{pokemonData.stats[5].base_stat}}
            <div class="barre">
              <div v-if="pokemonData.stats[5].base_stat <= 25" class="couleur1" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if="pokemonData.stats[5].base_stat > 25 & pokemonData.stats[5].base_stat < 50" class="couleur4" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[5].base_stat >= 50 & pokemonData.stats[5].base_stat <= 100" class="couleur2" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
              <div v-if= "pokemonData.stats[5].base_stat > 100" class="couleur3" :style="{width: pokemonData.stats[0].base_stat + 'px'}"></div>
            </div>
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
    </div>
  </div>
</template>

<style>
  .barre {
    width: 100px;
    border: 1px solid #000;
  }

  .couleur1 {
    height: 20px;
    background: red;
  }

  .couleur2 {
    height: 20px;
    background: green;
  }

  .couleur4 {
    height: 20px;
    background: orange;
  }

  .couleur3 {
    height: 20px;
    background: rgb(226,13,176);
    background: linear-gradient(45deg, rgba(226,13,176,1) 0%, rgba(121,9,112,1) 51%, rgba(0,212,255,1) 100%);
  }

  .center {
    display: flex;
    justify-content: center;
    align-items: center;
    height: calc(100vh - 10vh);
  }

  .grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }

  .icon {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>