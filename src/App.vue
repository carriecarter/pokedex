<template>
  <div id="app">
    <h1>Pokedex</h1>
    <Header/>
    <Results/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Results from './components/Results.vue'

export default {
  data() {
    return {

    };
  },
  components: {
    Header,
    Results
  }
};


</script>

<style>


</style>
