<script setup>
import { computed, onMounted, onUnmounted } from 'vue'

const props = defineProps(['product'])
const emit = defineEmits(['buy'])

onMounted(() => console.log("ProductDetails mounted"))
onUnmounted(() => console.log("ProductDetails unmounted"))

const discountedPrice = computed(() =>
  props.product.price -
  (props.product.price * props.product.discount) / 100
)

const buyNow = () => {
  emit('buy', props.product.id)
}
</script>

<template>
  <div class="p-6">
    <img :src="product.image" class="w-64 mb-4" />

    <h1 class="text-3xl font-bold">{{ product.name }}</h1>
    <p class="my-2">{{ product.description }}</p>

    <p class="font-bold">
  <span v-if="product.discount > 0">
    <span class="line-through text-gray-400 mr-2">
      ${{ product.price }}
    </span>
    <span class="text-green-500">
      ${{ discountedPrice }}
    </span>
  </span>

  <span v-else>
    ${{ product.price }}
  </span>
</p>

    <p>Stock: {{ product.stock }}</p>

    <div class="my-2">
      <span
        v-for="tag in product.tags"
        :key="tag"
        class="badge badge-outline mr-2"
      >
        {{ tag }}
      </span>
    </div>

    <button
      class="btn btn-success mt-4"
      :disabled="product.stock === 0"
      @click="buyNow"
    >
      {{ product.stock === 0 ? 'Out of Stock' : 'Buy Now' }}
    </button>
  </div>
</template>