<script setup lang="ts">
// Wir definieren mit TypeScript genau, wie ein Deal aussehen muss
defineProps<{
  deal: {
    id: number;
    name: string;
    condition: string;
    price: number;
  }
}>()
</script>

<template>
  <div class="deal-card">
    <h3>{{ deal.name }}</h3>
    <p>Zustand: <strong>{{ deal.condition }}</strong></p>
    <p>Preis: <span class="price">{{ deal.price }} €</span></p>
  </div>
</template>

<style scoped>
.deal-card {
  border: 2px solid #333;
  border-radius: 8px;
  padding: 15px;
  margin: 10px;
  background-color: #1e1e1e;
  color: white;
  width: 250px;
  text-align: left;
}
.price {
  color: #42b883;
  font-weight: bold;
  font-size: 1.2em;
}
</style>
