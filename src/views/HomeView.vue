<script setup lang="ts">
import { ref, onMounted } from 'vue'
import HardwareDeal from '../components/HardwareDeal.vue'

// Das <any[]> killt den "never"-Error
const deals = ref<any[]>([])

const loadDeals = () => {
  const endpoint = 'https://hardware-tracker-backend-it8g.onrender.com/deals'

  // Das { method: 'GET' } direkt hier drin killt den RequestInit-Error
  fetch(endpoint, { method: 'GET' })
    .then(response => response.json())
    .then(result => {
      deals.value = result
    })
    .catch(error => console.log('Fehler beim Fetchen:', error))
}

onMounted(() => {
  loadDeals()
})
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
