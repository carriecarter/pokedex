<template>
  <div class="tile" :class="pokemon.type_1">
    <div class="container">
      <img :src="pokemon.url_image" style="width:100%">
      <h3>{{ pokemon.pokemon }}</h3>
      <p><strong>Primary Type: </strong>{{ pokemon.type_1 }}</p>
      <p><strong>Secondary Type: </strong>{{ pokemon.type_2 }}</p>
      <p><strong>Speed: </strong>{{ pokemon.speed }}</p>
      <p><strong>Attack: </strong>{{ pokemon.attack }}</p>
      <p><strong>Defense: </strong>{{ pokemon.defense }}</p>
   
    </div>
  </div>
</template>

<script>
export default {
  props: ['pokemon']
};
</script>

<style>

.tile {
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    transition: 0.3s;
    width: 20%;
    border-radius: 5px;

}

.tile:hover {
    box-shadow: 0 80px 400px 0 rgba(0,0,0,0.2);
}

img {
    border-radius: 5px 5px 5px 5px;
    max-width: 200px;
    align-self: top center;
}

.container {
    padding: 2px 16px;
    display: flex;
    flex-direction:row;
}


</style>