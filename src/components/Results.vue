<template>
  <div>
    <hr>
    <Tile 
      v-for="pokemon in filteredPokemon"
      v-bind:key="pokemon.id"
      v-bind:pokemon="pokemon"
    /> 
  </div>
</template>

<script>
import Tile from './Tile.vue'

export default {
  data() {
    return {
      name: 'results'
    }
  },
  components: {
    Tile
  },
  props: ['filteredPokemon']
};

</script>

<style>

</style>