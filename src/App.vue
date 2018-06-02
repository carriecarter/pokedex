<template>
  <div id="app">
    <img src="./assets/Pokedex.png">
    <Header :filterPreferences="filterPreferences" :dedupedTypes="dedupedTypes" :sortPreferences="sortPreferences"/>  
    <Results :filteredPokemon="sortedPokemon"/>
      
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
          selectedType: null
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

  methods: {
    sortByString: function(items) {
      items.sort(function(a, b) {
        var nameA = a.name.toUpperCase(); // ignore upper and lowercase
        var nameB = b.name.toUpperCase(); // ignore upper and lowercase
        if (nameA < nameB) {
          return -1;
        }
        if (nameA > nameB) {
          return 1;
        }
          return 0;
      });
    }
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

    filteredPokemon: function() {
      let type = this.filterPreferences.selectedType;
      let minSpeed = this.filterPreferences.minSpeed;
      var filteredData = this.pokemonData.filter (pokemon => 
      (type === null || type === pokemon.type_1 || type === pokemon.type_2)
      && (minSpeed === 0 || minSpeed < pokemon.speed));
      return filteredData;
    },

    sortedPokemon: function() {
      switch(this.sortPreferences.selectedSort) {
        case 'name':
          return sortByString(this.filteredPokemon.slice());
          break;
        case 'speed':
          return this.filteredPokemon.slice().sort((a, b) => b.speed - a.speed);
          break;
        case 'type':
          
          break;
        default:
          return this.filteredPokemon.slice().sort((a, b) => b.speed - a.speed);

      }
    }
  }
}



</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}

</style>
