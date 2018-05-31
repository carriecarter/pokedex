<template>
  <div>
    <h1>Header</h1>
    <SearchFilter/>
    <Sort/>
  </div>
</template>

<script>
import SearchFilter from './SearchFilter.vue'
import Sort from './Sort.vue'
 
export default {
 data() {
   return {
     name: 'header'
   }
  },
  components: {
    SearchFilter,
    Sort
  }
};

</script>

<style>


</style>