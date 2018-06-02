<template>
  <div>
    <h2>Select your Pokemon's Qualities</h2>
    <label>Type</label>
    <select v-model="filterPreferences.selectedType">
      <option v-for="oneType in dedupedTypes"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
      </option>
    </select>
    <label>Minimum Speed</label>
    <input v-model="filterPreferences.minSpeed" type="number">
  </div>
</template>

<script>


export default {
  props: ['filterPreferences', 'dedupedTypes']
};

</script>

<style>


</style>