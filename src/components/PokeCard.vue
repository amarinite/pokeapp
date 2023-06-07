<script setup>
import axios from "axios";
import { ref } from "vue";

const { name, url } = defineProps(["name", "url"]);

const pokemon = ref(null);

const response = await axios.get(url);
pokemon.value = response.data;
</script>

<template>
  <div class="card">
    <h3>{{ name }}</h3>
    <img
      :src="pokemon.sprites.other['official-artwork'].front_default"
      :alt="name"
    />
    <p v-for="(type, index) in pokemon.types">
      {{ type.type.name }}
    </p>
  </div>
</template>

<style scoped>
.card {
  width: 12rem;
  min-height: 17rem;
  padding: 1rem;
  background-color: rgb(214, 252, 197);
  border-radius: 20px;
  box-shadow: 1px 1px 3px rgba(0, 0, 0, 0.295);
}

.card img {
  height: 8rem;
}
</style>
