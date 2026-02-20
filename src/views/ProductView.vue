<script setup>
import { computed, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'
import ProductDetails from '../components/ProductDetails.vue'
import ProductCard from '../components/ProductCard.vue'

// Props from App.vue
const props = defineProps(['products'])

// Emits up to App.vue
const emit = defineEmits(['buy'])

// Read ID from route
const route = useRoute()
const productId = Number(route.params.id)

// Current product
const product = computed(() =>
  props.products.find(p => p.id === productId)
)

// Related products = all except current
const relatedProducts = computed(() =>
  props.products.filter(p => p.id !== productId)
)

// Lifecycle hooks
onMounted(() => console.log(`ProductView mounted for ID: ${productId}`))
onUnmounted(() => console.log('ProductView unmounted'))

</script>

<template>
  <div v-if="product">
    <!-- Product details -->
    <ProductDetails
      :product="product"
      @buy="emit('buy', $event)"
    />

    <!-- Related products -->
    <h2 class="text-2xl font-bold mt-8 px-6">Related Products</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 p-6">
      <ProductCard
        v-for="item in relatedProducts"
        :key="item.id"
        :product="item"
      />
    </div>
  </div>

  <div v-else class="p-6">
    <p class="text-red-500 font-bold">Product not found.</p>
  </div>
</template>