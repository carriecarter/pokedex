<template>
  <div>
    <h1>Header</h1>
    <!-- <SearchFilter :dedupedTypes="dedupedTypes" :minSpeed="minSpeed" :selectedType="selectedType"/> -->
    <SearchFilter v-bind:minSpeed="minSpeed"/> 
    <Sort/>
  </div>
</template>

<script>
import SearchFilter from './SearchFilter.vue'
import Sort from './Sort.vue'

export default {

  props: ['minSpeed', 'dedupedTypes','selectedType'],

  components: {
    SearchFilter,
    Sort
  }
};

</script>

<style>


</style>