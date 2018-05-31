<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="selected">
      <option v-for="oneType in dedupeTypes()"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
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
  methods: {
    dedupeTypes() {
      const pokeTypes = new Set();
      this.pokemonData.forEach(element => {
        pokeTypes.add(element.type_1); 
      });
      return [...pokeTypes];
    }
  }
};

</script>

<style>


</style>