<template>
  <div id="app">
    <div class="pokemon-container">
      <PokemonList @pokemon-selected="displayPokemon" />
      <PokemonDetails :pokemon="selectedPokemon" />
    </div>
  </div>
</template>

<script>
import PokemonList from './components/PokemonList.vue';
import PokemonDetails from './components/PokemonDetails.vue';

export default {
  components: {
    PokemonList,
    PokemonDetails
  },
  data() {
    return {
      selectedPokemon: null,
    };
  },
  methods: {
    displayPokemon(pokemon) {
      this.selectedPokemon = pokemon; // מעדכנת את הפוקימון שנבחר
    },
  }
};
</script>

<style>
#app {
  font-family: Arial;
  text-align: center;
}

.pokemon-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 20px;
  width: 800px;
  margin: 20px auto;
  padding: 20px;
  border: 2px solid rgb(127, 79, 36);
  border-radius: 10px;
  background-color: #f5f5f5;
  box-shadow: 0 4px 8px rgb(127, 79, 36);

  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
