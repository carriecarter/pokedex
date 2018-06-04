<template>
  <div>
    <ul>
      <li>
        <div class="tile" :class="pokemon.type_1">
          <img :src="pokemon.url_image" style="width:150px">
           <div class="container">  
        <h3>{{ pokemon.pokemon }}</h3>
        <p><strong>Primary Type: </strong>{{ pokemon.type_1 }}</p>
        <p><strong>Secondary Type: </strong>{{ pokemon.type_2 }}</p>
        <p><strong>Speed: </strong>{{ pokemon.speed }}</p>
        <p><strong>Attack: </strong>{{ pokemon.attack }}</p>
        <p><strong>Defense: </strong>{{ pokemon.defense }}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['pokemon']
};
</script>

<style>

ul {
  list-style-type: none;
  display: flex;
  flex-direction: column;
}
p {
  line-height: 10px;
}
/* card styling credit to  https://www.w3schools.com/howto/howto_css_cards.asp */
.tile {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  margin: 10px;
  background-color: lightgrey;
  width: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  overflow-y:hidden;
}
.tile:hover {
  box-shadow: 0 80px 400px 0 rgba(0,0,0,0.2);
}
.container {
  padding: 2px 16px;
}


</style>