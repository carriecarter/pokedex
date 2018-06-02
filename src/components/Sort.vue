<template>
  <div>
    <form>
      <fieldset>
        <legend>Sort by</legend>
        <select v-model="sortPreferences.selectedSort">
          <option v-for="oneOption in sortPreferences.options"
            v-bind:key="oneOption" 
            v-bind:value="oneOption"
            selected="name">
            {{ oneOption }}
          </option>
        </select>
      </fieldset>
    </form> 
  </div>
</template>

<script>
export default {
  props: ['sortPreferences']
};
</script>

<style>

</style>