<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="selected">
      <option v-for="pokemon in pokemonData"
        v-bind:key="pokemon.id" 
        v-bind:value="pokemon.type_1">
        {{ pokemon.type_1 }}
      </option>
    </select>
    <span>Selected: {{ selected }}</span>
  </div>
</template>

<script>

import pokemonData from '../pokemon.js'

export default {
  data() {
    return { 
      pokemonData,
      selected: ''
    };
  },
};

</script>

<style>


</style>