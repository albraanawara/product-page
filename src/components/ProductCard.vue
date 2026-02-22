<script setup>
import { computed, onMounted, onUnmounted } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps(['product'])
const router = useRouter()

onMounted(() => console.log("ProductCard mounted"))
onUnmounted(() => console.log("ProductCard unmounted"))

const discountedPrice = computed(() => {
  const price = Number(props.product.price)
  const discount = Number(props.product.discount)

  return (price - (price * discount) / 100).toFixed(2)
})

const goToProduct = () => {
  router.push(`/product/${props.product.id}`)
}
</script>

<template>
  <div class="card bg-base-100 shadow-xl">
    <figure>
      <img :src="product.image" />
    </figure>

    <div class="card-body">
      <h2 class="card-title">
        {{ product.name }}
        <div v-if="product.badge" class="badge badge-secondary">
          {{ product.badge }}
        </div>
      </h2>

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

      <button class="btn btn-primary" @click="goToProduct">
        View Product
      </button>
    </div>
  </div>
</template>