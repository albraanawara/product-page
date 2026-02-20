<script setup>
import { onMounted, onUnmounted } from 'vue'
import CarouselBanner from '../components/CarouselBanner.vue'
import ProductCard from '../components/ProductCard.vue'

const props = defineProps(['products'])

onMounted(() =>
  console.log(`HomeView mounted — ${props.products.length} products loaded`)
)
onUnmounted(() => console.log("HomeView unmounted"))
</script>

<template>
  <CarouselBanner />

  <div class="grid grid-cols-1 md:grid-cols-3 gap-6 p-6">
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :product="product"
    />
  </div>
</template>