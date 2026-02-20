<script setup>
import { onMounted, onUnmounted } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps(['product'])
const router = useRouter()

onMounted(() => console.log("ProductCard mounted"))
onUnmounted(() => console.log("ProductCard unmounted"))

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

      <p>${{ product.price }}</p>

      <button class="btn btn-primary" @click="goToProduct">
        View Product
      </button>
    </div>
  </div>
</template>