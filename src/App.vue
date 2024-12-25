<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav class="bg-gray-800 p-4">
    <div class="container mx-auto flex space-x-4">
      <RouterLink
        to="/"
        class="rounded-md px-3 py-2 text-sm font-medium text-white hover:text-gray-300"
      >
        Home
      </RouterLink>
      <RouterLink
        to="/about"
        class="rounded-md px-3 py-2 text-sm font-medium text-white hover:text-gray-300"
      >
        About
      </RouterLink>
      <RouterLink
        to="/memory-leak"
        class="rounded-md px-3 py-2 text-sm font-medium text-white hover:text-gray-300"
      >
        Memory Leak
      </RouterLink>
    </div>
  </nav>
  <RouterView />
</template>

<style scoped></style>
