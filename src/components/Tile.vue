<template>
  <div class="tile" :class="pokemon.type_1">
    <h3>{{ pokemon.pokemon }}</h3>
    <p><strong>Primary Type: </strong>{{ pokemon.type_1 }}</p>
    <p><strong>Secondary Type: </strong>{{ pokemon.type_2 }}</p>
    <p><strong>Speed: </strong>{{ pokemon.speed }}</p>
    <p><strong>Attack: </strong>{{ pokemon.attack }}</p>
    <p><strong>Defense: </strong>{{ pokemon.defense }}</p>
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
  display: inline-block;
}

img {
  max-width: 100px;
  /* float: right; */
}
</style>