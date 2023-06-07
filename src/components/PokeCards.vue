<script setup>
import axios from "axios";
import { ref, watch } from "vue";

import PokeCard from "./PokeCard.vue";

const pokemons = ref(null);
const pokemon = ref(null);
const page = ref(0);
const pageLimit = 12;

const response = await axios.get(
  `https://pokeapi.co/api/v2/pokemon/?limit=${pageLimit}`
);
pokemons.value = response.data.results;

watch(page, async () => {
  const res = await axios.get(
    `https://pokeapi.co/api/v2/pokemon/?limit=${pageLimit}&offset=${
      page.value * pageLimit
    }`
  );
  pokemons.value = res.data.results;
});
</script>

<template>
  <div class="container">
    <h2>PokeCard</h2>
    <div class="cards">
      <PokeCard
        :key="pkmn.name"
        v-for="(pkmn, index) in pokemons"
        :name="pkmn.name"
        :url="pkmn.url"
      />
    </div>
    <div class="pagination">
      <button @click="page -= 1">Prev</button>
      <button @click="page += 1">Next</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  max-width: 55rem;
}

.cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
