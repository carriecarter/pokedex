<template>
  <div id="app">
    <h1>Pokedex</h1>
    <!-- <Header :dedupedTypes="dedupedTypes" :minSpeed="minSpeed" :selectedType="selectedType"/> -->
    <!-- <Header v-bind:minSpeed="minSpeed"/> -->
    <SearchFilter v-bind:minSpeed="minSpeed"/>
    <Results/>
      
  </div>
</template>

<script>
// import Header from './components/Header.vue'
import SearchFilter from './components/SearchFilter.vue'
import Results from './components/Results.vue'
import pokemonData from './pokemon.js'

export default {
  data() {
    return {
        pokemonData,
        dedupedTypes: [],
        selectedType: '',
        minSpeed: {
          value: 0
        }
    };
  },


  components: {
    // Header,
    Results,
    SearchFilter
  },

  methods: {

    // dedupeTypes() {
    //   const pokeTypeSet = new Set();
    //   this.pokemonData.forEach(pokemon => {
    //     pokeTypeSet.add(pokemon.type_1);
    //     pokeTypeSet.add(pokemon.type_2);
    //   });
    //   return [...pokeTypeSet];
    // },

    // filterPokemonData() {
      
    //   this.pokemonData.forEach(pokemon => {
    //     // if both filters apply
    //     if(this.selectedType && this.minSpeed) {
    //       if( (pokemon.type_1 === this.selectedType || pokemon.type_2 === this.selectedType) && pokemon.speed >= this.minSpeed) {
    //         this.filteredPokemon.push(pokemon);
    //       }
    //     } else if (this.selectedType) {
    //       if(pokemon.type_1 === this.selectedType || pokemon.type_2 === this.selectedType) {
    //         this.filteredPokemon.push(pokemon);
    //       }
    //     } else if (this.minSpeed) {
    //       if(this.minSpeed <= pokemon.speed) {
    //         this.filteredPokemon.push(pokemon);
    //       }
    //     }
    //   });
    //   console.log (this.filteredPokemon)
    //   if(this.filteredPokemon) {
    //     return this.filteredPokemon;
    //   } else {
    //     return this.pokemonData;
    //   }
      
    // }



  }
};


</script>

<style>


</style>
