<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <RouterView />
</template>

<style>
/* Reset und cleaner Darkmode für die ganze App */
body {
  margin: 0;
  padding: 0;
  background-color: #121212;
  color: #e0e0e0;
  font-family: sans-serif;
}

#app {
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
}
</style>
