# Hardware Deal Tracker (Frontend)

Eine moderne Single-Page-Application (SPA) auf Basis von Vue.js zum Tracken und Verwalten von PC-Hardware-Deals auf dem Gebrauchtmarkt. [cite_start]Entwickelt als Teil des Moduls Webtechnologien an der HTW Berlin (Milestone 2)[cite: 140, 142, 143].

## Tech-Stack
* [cite_start]**Framework:** Vue 3 (Composition API mit `<script setup>`) [cite: 305, 306]
* [cite_start]**Sprache:** TypeScript (für bessere Typsicherheit) [cite: 109, 170]
* [cite_start]**Build-Tool:** Vite [cite: 119, 124]
* [cite_start]**Router:** Vue Router für die Navigation [cite: 156, 184]
* [cite_start]**Testing:** Vitest für Unit-Tests [cite: 156, 186]

## Features (Milestone 2)
* [cite_start]Implementierung einer eigenen Komponente (`HardwareDeal.vue`) [cite: 282, 331]
* [cite_start]Dynamisches Rendering einer Liste von Hardware-Entitäten mittels `v-for` [cite: 439, 680]
* [cite_start]Saubere Trennung von Views und Komponenten [cite: 390, 392]

## Projekt starten

### 1. Abhängigkeiten installieren
[cite_start]Zuerst müssen alle benötigten npm-Pakete heruntergeladen werden[cite: 114, 163]:
```bash
npm install
Um den Code gemäß der Prettier-Vorgaben glattzubügeln:
npm run format

ntwicklungsserver starten
Startet die App lokal auf http://localhost:5173/:
npm run dev