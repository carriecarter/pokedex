<template>
  <div>
    <h1>Header</h1>
    <SearchFilter :filterPreferences="filterPreferences"/> 
    <Sort/>
  </div>
</template>

<script>
import SearchFilter from './SearchFilter.vue'
import Sort from './Sort.vue'

export default {

  props: ['filterPreferences', 'dedupedTypes'],

  components: {
    SearchFilter,
    Sort
  }
};

</script>

<style>


</style>