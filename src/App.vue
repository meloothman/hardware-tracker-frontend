<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <RouterView />
</template>

<style>
* {
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: Inter, system-ui, sans-serif;

  background:
    radial-gradient(circle at top left, #2563eb22, transparent 40%),
    radial-gradient(circle at bottom right, #7c3aed22, transparent 40%),
    #0f172a;

  color: #f8fafc;
}

#app {
  width: 100%;
  min-height: 100vh;
}

::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: #111827;
}

::-webkit-scrollbar-thumb {
  background: #374151;
  border-radius: 20px;
}

::-webkit-scrollbar-thumb:hover {
  background: #4b5563;
}

a {
  color: inherit;
}

input,
button {
  font-family: inherit;
}
</style>
