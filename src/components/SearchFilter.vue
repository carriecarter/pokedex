<template>
  <div>
    <h1>Select your Pokemon's Qualities</h1>
    <select v-model="filterPreferences.selectedType">
      <option v-for="oneType in dedupedTypes"
        v-bind:key="oneType" 
        v-bind:value="oneType">
        {{ oneType }}
      </option>
    </select>
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