<template>
  <div class="card">
    <h3>{{ deal.name }}</h3>
    <p><strong>Typ:</strong> {{ deal.type }}</p>
    <p><strong>Zustand:</strong> {{ deal.condition }}</p>
    <p><strong>Preis:</strong> {{ deal.price }} €</p>

    <div class="actions">
      <a :href="deal.link" target="_blank" rel="noopener" class="link-btn">Zum Deal</a>
      <button @click="deleteItem(deal.id)" class="delete-btn">Löschen</button>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{ deal: any }>()
const emit = defineEmits(['refresh'])

const deleteItem = (id: number) => {
  fetch(`https://hardware-tracker-backend-it8g.onrender.com/deals/${id}`, {
    method: 'DELETE'
  })
    .then(() => {
      emit('refresh')
    })
    .catch(err => console.error('Löschen fehlgeschlagen:', err))
}
</script>

<style scoped>
.card {
  background: rgba(255,255,255,0.05);

  backdrop-filter: blur(15px);

  border: 1px solid rgba(255,255,255,0.08);

  border-radius: 20px;

  padding: 20px;

  transition: .25s;
}

.card:hover {
  transform: translateY(-5px);

  border-color:
    rgba(59,130,246,.4);

  box-shadow:
    0 15px 35px rgba(0,0,0,.35);
}

.card h3 {
  margin-top: 0;
  margin-bottom: 15px;
}

.card p {
  color: #d1d5db;
  margin: 8px 0;
}

.actions {
  display: flex;
  gap: 10px;
  margin-top: 20px;
}

.link-btn {
  flex: 1;

  text-align: center;

  text-decoration: none;

  padding: 10px;

  border-radius: 10px;

  color: white;

  font-weight: 600;

  background: #2563eb;

  transition: .2s;
}

.link-btn:hover {
  background: #1d4ed8;
}

.delete-btn {
  border: none;

  padding: 10px 14px;

  border-radius: 10px;

  cursor: pointer;

  color: white;

  background: #dc2626;

  transition: .2s;
}

.delete-btn:hover {
  background: #b91c1c;
}
</style>
