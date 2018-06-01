<template>
  <div class="tile" :class="pokemon.type_1">
    <h3>{{ pokemon.pokemon }}</h3>
    <p>{{ pokemon.type_1 }}</p>
    <img :src="pokemon.url_image">
    
 
  </div>
</template>

<script>

export default {
  props: ['pokemon']
};
</script>

<style>

.grass {
  background-color: green;
}

.tile {
  max-width: 400px;
  padding: 6px;
  margin: 10px;
  border-radius: 20px;
  border: solid 4px grey;
}

img {
  max-width: 100px;
  float: right;
}
</style>