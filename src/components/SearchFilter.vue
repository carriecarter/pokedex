<template>
  <div>
    <form>
      <fieldset>
        <legend>Choose your Pokemon qualities</legend>
        Type <select v-model="filterPreferences.selectedType">
          <option v-for="oneType in typeOptions"
            v-bind:key="oneType" 
            v-bind:value="oneType"
            selected="all">
            {{ oneType }}
          </option>
        </select>
        Minimum Speed <input v-model="filterPreferences.minSpeed" type="number" max="500">
        Minimum Attack <input v-model="filterPreferences.minAttack" type="number" max="500">
        Minimum Defense <input v-model="filterPreferences.minDefense" type="number" max="500">
      </fieldset>
    </form>
  </div>
</template>

<script>
export default {
  props: ['filterPreferences', 'typeOptions']
};
</script>

<style>


</style>