<script setup lang="ts">
import { ref } from 'vue'
import HardwareDeal from '../components/HardwareDeal.vue'

// Hardcodierte Beispiel-Daten für Milestone 2
const deals = ref([
  { id: 1, name: "AMD Ryzen 7 3700X", condition: "Gebraucht - eBay", price: 85.0 },
  { id: 2, name: "Nvidia RTX 3060", condition: "Gebraucht - Kleinanzeigen", price: 220.0 },
  { id: 3, name: "Kingston Fury DDR4 (KF436C17BB2A/8)", condition: "Neu - Mindfactory", price: 25.0 }
])
</script>

<template>
  <main>
    <h1>Hardware Deal Tracker</h1>
    <div class="deal-container">
      <HardwareDeal
        v-for="item in deals"
        :key="item.id"
        :deal="item"
      />
    </div>
  </main>
</template>

<style scoped>
main {
  text-align: center;
  padding: 20px;
  font-family: sans-serif;
}
.deal-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
  margin-top: 20px;
}
</style>
