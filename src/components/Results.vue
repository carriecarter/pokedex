<template>
  <div>
    <h1>Results</h1>
    <Tile/>    
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
  }
};

</script>

<style>

</style>