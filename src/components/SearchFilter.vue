<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="selectedType">
      <option v-for="oneType in dedupedTypes"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
      </option>
    </select>
    <span>Selected: {{ selectedType }}</span>
    <input v-model="minSpeed.value" type="number">
    <span>Min speed: {{ minSpeed }}</span>
    <!-- <button v-on:click="filterPokemonData">Filter</button> -->
  </div>
</template>

<script>


export default {
  props: ['minSpeed', 'dedupedTypes','selectedType']
};

</script>

<style>


</style>