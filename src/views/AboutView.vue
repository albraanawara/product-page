<script setup>
import { onMounted, onUnmounted } from 'vue'

onMounted(() => console.log("AboutView mounted"))
onUnmounted(() => console.log("AboutView unmounted"))
</script>

<template>
  <div class="p-6">
    <h1 class="text-3xl font-bold">Albraa Nawara</h1>
    <h2 class="text-xl mt-2">VueJS Course — ITI</h2>

    <p class="mt-4">
      This store is a multi-page SPA built with Vue Router,
      props, emits, and lifecycle hooks.
    </p>
  </div>
</template>
