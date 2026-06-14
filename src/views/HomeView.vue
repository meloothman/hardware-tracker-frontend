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
<style scoped>
main {
  max-width: 1200px;
  margin: auto;
  padding: 40px 20px;
}

h1 {
  text-align: center;
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 10px;

  background: linear-gradient(
    90deg,
    #3b82f6,
    #8b5cf6
  );

  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.subtitle {
  text-align: center;
  color: #94a3b8;
  margin-bottom: 40px;
}

.form-container {
  display: grid;
  grid-template-columns:
    repeat(auto-fit, minmax(250px, 1fr));

  gap: 15px;

  padding: 25px;

  margin-bottom: 40px;

  background: rgba(255,255,255,0.05);

  backdrop-filter: blur(15px);

  border-radius: 20px;

  border: 1px solid rgba(255,255,255,0.1);
}

.form-container h3 {
  grid-column: 1 / -1;
  margin: 0;
}

input {
  padding: 14px;

  border-radius: 12px;

  border: 1px solid rgba(255,255,255,0.1);

  background: rgba(255,255,255,0.08);

  color: white;

  font-size: 14px;
}

input:focus {
  outline: none;

  border-color: #3b82f6;

  box-shadow:
    0 0 15px rgba(59,130,246,.4);
}

button {
  grid-column: 1 / -1;

  border: none;

  border-radius: 12px;

  padding: 14px;

  font-weight: 700;

  cursor: pointer;

  color: white;

  background:
    linear-gradient(
      135deg,
      #2563eb,
      #7c3aed
    );

  transition: .2s;
}

button:hover {
  transform: translateY(-2px);
}

.deal-container {
  display: grid;

  grid-template-columns:
    repeat(auto-fill, minmax(320px, 1fr));

  gap: 20px;
}
</style>
