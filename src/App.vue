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
    sortByString: function(items, property) {
      items.sort(function(a, b) {
        var stringA = a[property].toUpperCase();
        var stringB = b[property].toUpperCase();
        if (stringA < stringB) {
          return -1;
        }
        if (stringA > stringB) {
          return 1;
        }
          return 0;
      });
      return items;
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
          return this.sortByString(this.filteredPokemon.slice(), 'pokemon');
          break;
        case 'speed':
          return this.filteredPokemon.slice().sort((a, b) => b.speed - a.speed);
          break;
        case 'type':
          return this.sortByString(this.filteredPokemon.slice(), 'type_1');
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
