<script setup>
import PokeCards from "./components/PokeCards.vue";
</script>

<template>
  <main>
    <h1>PokeApp</h1>
    <Suspense>
      <template #default><PokeCards /></template>
      <template #fallback>
        <div><p>Loading...</p></div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
