<script setup>
const { name, image, types } = defineProps(["name", "image", "types"]);
</script>

<template>
  <div class="card">
    <h3>{{ name }}</h3>
    <img :src="image" alt="" />
    <span v-for="type in types">{{ type }}</span>
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
  height: 4rem;
}
</style>
