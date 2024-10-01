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


  <div class="p-8">
    <div class="text-center my-14 border border-2 border-black p-6">
        <h3 class="font-bold text-warning">This is Button</h3>
        <Button variant="warning" >Click me</Button>
    </div>


    <div class="text-center my-14 border border-2 border-black p-6">
        <h3 class="font-bold">This is input</h3>
    <Input  type="text" placeholder="Search..." class="pl-10" />

    
    </div>

    <div class="text-center my-14 border border-2 border-black p-6">
        <h3 class="font-bold">This is Accordian</h3>
        <Accordian />
    </div>
   

    <div class="text-center my-14 border border-2 p-6 border-black">
        <h3 class="font-bold">This is Alert</h3>
        <Alert />
    </div>
   

    <div class="text-center my-14 border border-2 p-6 border-black">
        <h3 class="font-bold">This is Dialog</h3>
        <Dialog />
    </div>
    
    <div class="text-center my-14 border border-2 p-6 border-black">
        <h3 class="font-bold">This is Card</h3>
        <Card />
    </div>
</div>
    </div>
  
</template>
