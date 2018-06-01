<template>
  <div>
    <h1>Header</h1>
    <SearchFilter :filteredPokemon="filteredPokemon"/>
    <ul>
      <li v-for="pokemon in filteredPokemon"
          v-bind:key="pokemon.id">{{ pokemon.pokemon }}
      </li>
    </ul>
    <Sort/>
  </div>
</template>

<script>
import SearchFilter from './SearchFilter.vue'
import Sort from './Sort.vue'

export default {
 data() {
   return {
     name: 'header',
     filteredPokemon: []
   }
  },

  components: {
    SearchFilter,
    Sort
  }
};

</script>

<style>


</style>