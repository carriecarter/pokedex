<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="selectedType">
      <option v-for="oneType in dedupeTypes()"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
      </option>
    </select>
    <span>Selected: {{ selectedType }}</span>
    <input v-model="minSpeed" placeholder="enter min speed">
    <span>Min speed: {{ minSpeed }}</span>
    <button v-on:click="filterPokemonData">Filter</button>
  </div>
</template>

<script>
import pokemonData from '../pokemon.js'

export default {
  data() {
    return {
      pokemonData,
      selectedType: '',
      minSpeed: 0
      //filterPokemonData();
    };
  },

  // props: {
  //   selectedType: String,
  //   minSpeed: Number
  // },

  methods: {

    dedupeTypes() {
      const pokeTypeSet = new Set();
      this.pokemonData.forEach(pokemon => {
        pokeTypeSet.add(pokemon.type_1);
        pokeTypeSet.add(pokemon.type_2);
      });
      return [...pokeTypeSet];
    },

    filterPokemonData() {
      let filteredPokemon = [];
      this.pokemonData.forEach(pokemon => {
        // if both filters apply
        if(this.selectedType && this.minSpeed) {
          if( (pokemon.type_1 === this.selectedType || pokemon.type_2 === this.selectedType) && pokemon.speed >= this.minSpeed) {
            filteredPokemon.push(pokemon);
          }
        } else if (this.selectedType) {
          if(pokemon.type_1 === this.selectedType || pokemon.type_2 === this.selectedType) {
            filteredPokemon.push(pokemon);
          }
        } else if (this.minSpeed) {
          if(this.minSpeed <= pokemon.speed) {
            filteredPokemon.push(pokemon);
          }
        }
      });
      console.log (filteredPokemon)
      if(filteredPokemon) {
        return filteredPokemon;
      } else {
        return this.pokemonData;
      }
      
    }



  }
};

</script>

<style>


</style>