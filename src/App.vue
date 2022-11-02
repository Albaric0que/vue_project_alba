<template>
  <header class="container">
    <div class="row">
      <div class="col-md-12 text-center">
        <h1 class="title my-4">Pokédex</h1>
      </div>
      <div class="row">
        <form id="searchForm" class="form-inline col-md-8 offset-md-2">
          <div class="form-group mb-2 mr-2">
            <input
              v-model="pokemonId"
              type="text"
              class="form-control"
              id="name"
              placeholder="Introduce el id o nombre del pokemon"
            />
          </div>
          <button
            @click="searchPokemon"
            type="submit"
            class="btn btn-secondary mb-2"
          >
            Buscar
          </button>
        </form>
      </div>
      <div class="col-md-12">
        <div class="row card-container"></div>
      </div>
    </div>
  </header>
</template>

<script>
/* import { pokeapi } from "@/api/pokeapi"; */

export default {
  name: "app",

  data() {
    return {
      pokemonData: {},
      pokemonId: "",
    };
  },

  methods: {
    async searchPokemon() {
      try {
        const pokemonToFind = await fetch(
          `https://pokeapi.co/api/v2/pokemon/${this.pokemonId}`
        );
        const pokemon = await pokemonToFind.json();
        this.pokemonData = pokemon;
        console.log(pokemon);
        return pokemon;
      } catch (error) {
        alert("Pokemon not found");
      }
    },
  },
};
</script>
