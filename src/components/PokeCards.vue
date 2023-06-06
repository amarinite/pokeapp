<script setup>
import axios from "axios";

const response = await axios.get("https://pokeapi.co/api/v2/pokemon/");

console.log(response);
</script>

<template>
  <h2>PokeCards</h2>
</template>
