<template>
  <div id="app">
    <h1>Pokedex</h1>
    <Header :filterPreferences="filterPreferences" :dedupedTypes="dedupedTypes" :sortPreferences="sortPreferences"/>  
    <Results :filteredPokemon="filteredPokemon"/>
      
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Results from './components/Results.vue'
import pokemonData from './pokemon.js'

export default {
  data() {
    return {
        pokemonData,
        filterPreferences: {
          minSpeed: 0,
          selectedType: ''
        },
        sortPreferences: {
          options: ['name','speed', 'type'],
          selectedSort: ''
        }
    };
  },


  components: {
    Header,
    Results,
  },

  computed: {
    dedupedTypes: function() {
      const pokeTypeSet = new Set();
      this.pokemonData.forEach(pokemon => {
        pokeTypeSet.add(pokemon.type_1);
        pokeTypeSet.add(pokemon.type_2);
      });
      return [...pokeTypeSet];
    },
    // sortedPokemon: function() {
    //   this.filteredPokemon.sort((a, b) => b.pokemon - a.pokemon);
    //   return filteredPokemon;
    // },
    filteredPokemon: function() {
      return this.pokemonData.filter(pokemon => {
        return (this.selectedType === '' || this.selectedType === pokemon.type_1 || this.selectedType === pokemon.type_2)
          && (this.filterPreferences.minSpeed < 0 || this.filterPreferences.minSpeed < this.pokemon.speed);
      });
    }
  }
}


    // filterPokemonData() {
      
    //   this.pokemonData.forEach(pokemon => {
    //     // if both filters apply
    //     if(this.selectedType && this.minSpeed) {
    //       if( (pokemon.type_1 === this.selectedType || pokemon.type_2 === this.selectedType) && pokemon.speed >= this.minSpeed) {
    //         this.filteredPokemon.push(pokemon);
    //       }
    //     } else if (this.) {
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



</script>

<style>


</style>
