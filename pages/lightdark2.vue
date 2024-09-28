<template>
    <div :class="darkMode ? 'dark' : ''" class="page-container">
      <button @click="toggleDarkMode">
        Toggle Dark Mode
      </button>
      <div class="content">
        This is the Light/Dark Mode page with CSS variables.
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const darkMode = ref(false)
  
  const toggleDarkMode = () => {
    darkMode.value = !darkMode.value
  }
  </script>
  
  <style scoped>
  .page-container {
    --bg-color: #ffffff;
    --text-color: #000000;
    background-color: var(--bg-color);
    color: var(--text-color);
    padding: 20px;
  }
  
  button {
    background-color: var(--bg-color);
    color: var(--text-color);
    padding: 10px;
    border: 1px solid var(--text-color);
    cursor: pointer;
  }
  
  .dark {
    --bg-color: #000000;
    --text-color: #ffffff;
  }
  </style>
  