<script setup lang="ts">
import { ref, onMounted } from 'vue'
import HardwareDeal from '../components/HardwareDeal.vue'

// Das <any[]> killt den "never"-Error
const deals = ref<any[]>([])

// --- NEU FÜR M4: Variablen für das Formular ---
const newName = ref('')
const newType = ref('')
const newPrice = ref(0)

// Den Endpoint packen wir nach oben, damit GET und POST ihn nutzen können
const endpoint = 'https://hardware-tracker-backend-it8g.onrender.com/deals'

const loadDeals = () => {
  // Das { method: 'GET' } direkt hier drin killt den RequestInit-Error
  fetch(endpoint, { method: 'GET' })
    .then(response => response.json())
    .then(result => {
      deals.value = result
    })
    .catch(error => console.log('Fehler beim Fetchen:', error))
}

// --- NEU FÜR M4: Die POST-Methode, um Deals in die DB zu schießen ---
const submitDeal = () => {
  const newDeal = {
    name: newName.value,
    type: newType.value,
    price: newPrice.value
  }

  fetch(endpoint, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(newDeal)
  })
    .then(response => response.json())
    .then(() => {
      // Wenn gespeichert: Felder wieder leeren und Liste sofort neu laden
      newName.value = ''
      newType.value = ''
      newPrice.value = 0
      loadDeals()
    })
    .catch(error => console.log('Fehler beim POST:', error))
}

onMounted(() => {
  loadDeals()
})
</script>

<template>
  <main>
    <h1>Hardware Deal Tracker</h1>

    <div class="form-container">
      <h3>Neuen Deal eintragen</h3>
      <input v-model="newName" placeholder="Hardware (z.B. RTX 4090)" />
      <input v-model="newType" placeholder="Typ (z.B. GPU)" />
      <input v-model="newPrice" type="number" placeholder="Preis in €" />
      <button @click="submitDeal">Speichern</button>
    </div>

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

/* --- NEU FÜR M4: Styling fürs Formular --- */
.form-container {
  margin: 20px auto;
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  background-color: #f9f9f9;
}

.deal-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
  margin-top: 20px;
}
</style>
