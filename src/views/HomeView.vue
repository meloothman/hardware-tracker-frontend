<script setup lang="ts">
import { ref, onMounted } from 'vue'
import HardwareDeal from '../components/HardwareDeal.vue'

const deals = ref<any[]>([])

const newName = ref('')
const newType = ref('')
const newPrice = ref(0)
const newCondition = ref('')
const newLink = ref('')

const endpoint = 'https://hardware-tracker-backend-it8g.onrender.com/deals'

const loadDeals = () => {
  fetch(endpoint)
    .then(res => res.json())
    .then(data => (deals.value = data))
    .catch(err => console.error(err))
}

const submitDeal = () => {
  if (!newName.value.trim()) return

  fetch(endpoint, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      name: newName.value,
      type: newType.value,
      price: newPrice.value,
      condition: newCondition.value,
      link: newLink.value
    })
  }).then(() => {
    newName.value = ''
    newType.value = ''
    newPrice.value = 0
    newCondition.value = ''
    newLink.value = ''
    loadDeals()
  })
}

onMounted(loadDeals)
</script>

<template>
  <main>
    <h1>🔥 Hardware Deal Tracker</h1>

    <p class="subtitle">
      Finde, speichere und vergleiche Hardware-Schnäppchen
    </p>

    <div class="form-container">
      <h3>Neuen Deal hinzufügen</h3>

      <input v-model="newName" placeholder="Hardware Name" />
      <input v-model="newType" placeholder="Typ (GPU, CPU, RAM ...)" />
      <input v-model="newPrice" type="number" placeholder="Preis in €" />
      <input v-model="newCondition" placeholder="Zustand" />
      <input v-model="newLink" placeholder="Link zum Deal" />

      <button @click="submitDeal">
        Deal speichern
      </button>
    </div>

    <div class="deal-container">
      <HardwareDeal
        v-for="d in deals"
        :key="d.id"
        :deal="d"
        @refresh="loadDeals"
      />
    </div>
  </main>
</template>

<style scoped>

</style>
