<template>
  <div id="app">
    <img src="./assets/Pokedex.png">
    <Header :filterPreferences="filterPreferences" :typeOptions="dedupedTypes" :sortPreferences="sortPreferences"/>  
    <Results :listToDisplay="sortedPokemon"/>
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
        minAttack: 0,
        minDefense: 0,
        selectedType: 'all'
      },
      sortPreferences: {
        options: ['name','speed', 'primary type', 'attack', 'defense'],
        selectedSort: 'name',
        // directionOptions: ['ascending', 'descending'],
        // selectedDirection: 'ascending'
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
        if(pokemon.type_2 != 'NA') {pokeTypeSet.add(pokemon.type_2)};
      });
      const pokeTypes = [...pokeTypeSet];
      this.sortStrings(pokeTypes);
      pokeTypes.unshift('all');
      return pokeTypes;
    },

    filteredPokemon: function() {
      let type = this.filterPreferences.selectedType;
      let minSpeed = this.filterPreferences.minSpeed;
      let minAttack = this.filterPreferences.minAttack;
      let minDefense = this.filterPreferences.minDefense;
      var filteredList = this.pokemonData.filter (pokemon => 
      (type === null || type === 'all' || type === pokemon.type_1 || type === pokemon.type_2)
      && (minSpeed === 0 || minSpeed <= pokemon.speed)
      && (minAttack === 0 || minAttack <= pokemon.attack)
      && (minDefense === 0 || minDefense <= pokemon.defense));
      return filteredList;
    },

    sortedPokemon: function() {
      const listToSort = this.filteredPokemon.slice();
      switch(this.sortPreferences.selectedSort) {
        case 'name':
          return this.sortOnStringProperty(listToSort, 'pokemon');
          break;
        case 'speed':
          return listToSort.sort((a, b) => a.speed - b.speed);
          break;
        case 'primary type':
          return this.sortOnStringProperty(listToSort, 'type_1');
          break;
        case 'attack':
          return listToSort.sort((a, b) => a.attack - b.attack);
          break;
        case 'defense':
          return listToSort.sort((a, b) => a.defense - b.defense);
          break;
        default:
          return this.sortOnStringProperty(listToSort, 'pokemon');
      }
    }

  },
  
  methods: {

    sortOnStringProperty: function(objectArray, property) {
      objectArray.sort(function(a, b) {
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
      return objectArray;
    },

    sortStrings: function(array) {
      array.sort(function(a, b) {
        var stringA = a.toUpperCase();
        var stringB = b.toUpperCase();
        if (stringA < stringB) {
          return -1;
        }
        if (stringA > stringB) {
          return 1;
        }
          return 0;
      });
      return array;
    }

  }

}



</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}

</style>
