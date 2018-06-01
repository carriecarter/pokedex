<template>
  <div>
    <h1>Sort By: </h1>
    <select v-model="sortPreferences.selectedSort">
      <option v-for="oneOption in sortPreferences.options"
        v-bind:key="oneOption" 
        v-bind:value="oneOption">
        {{ oneOption }}
      </option>
    </select>
    
  </div>
</template>

<script>


export default {
  props: ['sortPreferences']
};

</script>

<style>


</style>