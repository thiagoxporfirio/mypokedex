
<template>
  <div class="container">
      <h1>POKEMON`S</h1>
      <PokemonList :imageUrl="imageUrl" :apiUrl="apiUrl" />
  </div>
</template>

<script setup>
import PokemonList from './components/PokemonList.vue';
import PokemonDetail from './components/PokemonDetail.vue';
import PokemonSearch from './components/PokemonSearch.vue';

  export default {

    data: () => {
      return{
        imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
        apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
      }
    },
    components: {
      PokemonDetail,
      PokemonList,
      PokemonSearch
    }
    
  }


</script>

<style scoped>

</style>
