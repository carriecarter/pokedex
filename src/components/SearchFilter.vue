<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="filterPreferences.selctedType">
      <option v-for="oneType in dedupedTypes"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
      </option>
    </select>
    <span>Selected: {{ filterPreferences.selctedType }}</span>
    <input v-model="filterPreferences.minSpeed" type="number">
    <span>Min speed: {{ filterPreferences.minSpeed }}</span>
    <!-- <button v-on:click="filterPokemonData">Filter</button> -->
  </div>
</template>

<script>


export default {
  props: ['filterPreferences', 'dedupedTypes']
};

</script>

<style>


</style>