<script setup>
import { useState } from '#app'

const darkMode = useState('darkMode', () => false)

const toggleDarkMode = () => {
  darkMode.value = !darkMode.value
  if (darkMode.value) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}
</script>

<template>
    <div class="p-6">
        <button class="border border-black" @click="toggleDarkMode">
    Toggle Dark Mode
  </button>
  <div class="p-4 bg-white text-black dark:bg-black dark:text-white">
    This is a dark mode/light mode example.
  </div>
    </div>
  
</template>
