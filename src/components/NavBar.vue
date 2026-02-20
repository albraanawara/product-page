<script setup>
import { onMounted, onUnmounted } from 'vue'
import { RouterLink } from 'vue-router'

defineProps(['totalStock'])

onMounted(() => console.log("NavBar mounted"))
onUnmounted(() => console.log("NavBar unmounted"))
</script>

<template>
  <div class="navbar bg-base-200 px-6">
    <RouterLink to="/" class="btn btn-ghost">Home</RouterLink>
    <RouterLink to="/product/1" class="btn btn-ghost">Product</RouterLink>
    <RouterLink to="/about" class="btn btn-ghost">About</RouterLink>

    <div class="ml-auto font-bold">
      Total Stock: {{ totalStock }}
    </div>
  </div>
</template>