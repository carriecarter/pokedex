<template>
  <div>
    <SearchFilter :filterPreferences="filterPreferences" :typeOptions="typeOptions"/> 
    <Sort :sortPreferences="sortPreferences"/>
  </div>
</template>

<script>
import SearchFilter from './SearchFilter.vue'
import Sort from './Sort.vue'

export default {

  props: ['filterPreferences', 'typeOptions', 'sortPreferences'],

  components: {
    SearchFilter,
    Sort
  }

};

</script>

<style>


</style>