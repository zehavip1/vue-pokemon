<template>
    <div v-if="pokemon" class="pokemon-details-container">
      <img :src="pokemon.img" alt="Pokemon Image" class="pokemon-img" />
      <div><strong>Types:</strong> {{ pokemon.types }}</div>
      <div><strong>Description:</strong> {{ pokemon.description }}</div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PokemonDetails',
    props: {
      pokemon: Object,
    },
  };
  </script>
  
  <style>
  .pokemon-details-container {
    width: 400px;
    text-align: left;
    border: 1px solid rgb(127, 79, 36);
    padding: 15px;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 2px 4px rgb(127, 79, 36);
  }
  
  .pokemon-img {
    max-width: 100%;
    display: block;
    margin: 0 auto 10px;
  }
  
  .pokemon-info {
    font-size: 14px;
  }
  </style>
  