<template>
  <div>
    <h3>{{listToDisplay.length}} pokemon met your criteria</h3>
    <Tile 
      v-for="pokemon in listToDisplay"
      v-bind:key="pokemon.id"
      v-bind:pokemon="pokemon"
    /> 
  </div>
</template>

<script>
import Tile from './Tile.vue'

export default {
  components: {
    Tile
  },
  props: ['listToDisplay']
};

</script>
