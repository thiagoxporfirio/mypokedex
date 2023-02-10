<template>
  <div class="container">
    <h1>POKEDEX</h1>
    <PokemonSearch :apiUrl="apiUrl" @setPokemonUrl="setPokemonUrl" />
    <PokemonList :imageUrl="imageUrl" :apiUrl="apiUrl" @setPokemonUrl="setPokemonUrl" />
    <PokemonDetail v-if="showDetail" :pokemonUrl="pokemonUrl" :imageUrl="imageUrl" @closeDetail="closeDetail" />
  </div>
</template>
  
<script>
import PokemonSearch from './PokemonSearch.vue';
import PokemonDetail from './PokemonDetail.vue';
import PokemonList from './PokemonList.vue';

export default {

  data: () => {
    return {
      imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/',
      apiUrl: 'https://pokeapi.co/api/v2/pokemon/',
      pokemonUrl: '',
      showDetail: false
    }
  },
  components: {
    PokemonSearch,
    PokemonList,
    PokemonDetail,
    
  },
  methods: {
    setPokemonUrl(url) {
      this.pokemonUrl = url
      this.showDetail = true
    },
    closeDetail() {
      this.pokemonUrl = ''
      this.showDetail = false
    }
  }

}
</script>
  
<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@500&display=swap');

.container {

  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  width: calc(100% - 20px);
  min-height: calc(100vh - 20px);
  background: radial-gradient(#0074ff, #20dac0);
  font-family: 'Nunito', sans-serif;
  font-size: 1rem;
  font-weight: normal;

}

h1 {
  color: #fff;
  background: #f1efed;
  box-shadow: 0 15px 30px rgba(0, 0, 0, .2),
    0 10px 10px rgba(0, 0, 0, .2);
  padding: 20px;
  border-radius: 18px;
  color: #120907;
  border: 1px solid rgba(0, 0, 0, 0.8);
}
</style>