<template>
  <div class="card-box">
    <a class="remove-btn" href="#" @click.prevent="emitRemove">X</a>
    <img class="photo" :src="pokemon.pokeID" :alt="pokemon.pokeName" />
    <h2 class="name mb-2">{{ pokemon.pokeName }}</h2>
    <ul class="type-list" v-for="item in pokemon.pokeType">
      <li class="type-item" :class="item.type.name">
        {{ item.type.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    pokemon: Object,
  },
  emits: ["remove"],
  methods: {
    emitRemove() {
      this.$emit("remove", this.pokemon.internalId);
    },
  },
};
</script>
