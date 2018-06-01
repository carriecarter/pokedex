<template>
  <div id="app">
    <h1>Pokedex</h1>
    <Header :filteredPokemon="filteredPokemon"/>
    <Results/>
      
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Results from './components/Results.vue'

export default {
  data() {
    return {
      filteredPokemon: []
    };
  },
  // props: ['filteredPokemon'],

  components: {
    Header,
    Results
  }
};


</script>

<style>


</style>
