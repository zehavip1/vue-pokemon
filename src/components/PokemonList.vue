<template>
    <div class="pokemon-list-container">
      <h3>Pokémon List</h3>
      <ul>
        <li
          v-for="pokemon in pokemons"
          :key="pokemon.id"
          @click="selectPokemon(pokemon)"
        >
          {{ pokemon.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PokemonList',
    // props:{
    //     selectPokemon:Array
    // },
    data() {
      return {
        pokemons: [],
      };
    },
    mounted() {
      this.fetchPokemons();
    },
    methods: {
      async fetchPokemons() {
        const pokemonCount = 300; // הגבלה לשלושה פוקימונים לדוגמה
        for (let i = 1; i <= pokemonCount; i++) {
          const res = await fetch(`https://pokeapi.co/api/v2/pokemon/${i}`);
          const data = await res.json();
  
          const speciesRes = await fetch(data.species.url);
          const speciesData = await speciesRes.json();
  
          this.pokemons.push({
            id: i,
            name: data.name,
            img: data.sprites.front_default,
            types: data.types.map((type) => type.type.name).join(', '),
            description:speciesData.flavor_text_entries[9].flavor_text,
          });

        //   if (id=== 1) {
        //       this.selectPokemon=this.pokemons[0];
        //     }

        }
      },
      selectPokemon(pokemon) {
        this.$emit('pokemon-selected', pokemon);
      },
    },
  };
  </script>
  
  <style>
  h3{
    color: rgb(127, 79, 36);
  }
  .pokemon-list-container {
    width: 300px;
    height: 400px;
    border: 1px solid rgb(127, 79, 36);
    border-radius: 8px;
    padding: 10px;
    overflow-y: auto;
    background-color: #f9f9f9;
    box-shadow: 0 2px 4px rgb(127, 79, 36);
  }
  
  ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  
  li {
    cursor: pointer;
    color:  rgb(182, 173, 144);
    margin: 5px 0;
    transition: color 0.3s ease;
  }
  
  li:hover {
    color:rgb(166, 138, 100);
    font-weight: bold;
  }
  </style>
  