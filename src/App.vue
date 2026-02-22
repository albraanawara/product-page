<script setup>
import { ref, computed } from 'vue'
import NavBar from './components/NavBar.vue'
import { RouterView } from 'vue-router'

const products = ref([
  {
    id: 1,
    name: "Cozy Sneakers",
    description: "High-quality sneakers that go with everything you wear.",
    image: "https://cdn.clothbase.com/uploads/4734bf57-d2e8-4345-8947-574e85d9039a/beige-cozy-sneakers.jpg",
    badge: "NEW",
    price: 120,
    discount: 20,
    stock: 10,
    tags: ["Fashion", "Casual", "Sport"]
  },
  {
    id: 2,
    name: "Running Shoes",
    description: "Built for speed and comfort on any terrain.",
    image:"https://contents.mediadecathlon.com/p3064111/k$d9be965d40017be5509e327b0ecff4ed/jogflow-1901-men-s-running-shoes-blackslashgrey.jpg"
,
    badge: "",
    price: 90,
    discount: 10,
    stock: 5,
    tags: ["Sport", "Running"]
  },
  {
    id: 3,
    name: "Casual Boots",
    description: "Rugged boots for everyday adventures.",
    image: "https://m.media-amazon.com/images/I/71YDLDU709L._AC_UY900_.jpg",
    badge: "SALE",
    price: 150,
    discount: 50,
    stock: 8,
    tags: ["Casual", "Winter"]
  },
  {
    id: 4,
    name: "Flip Flops",
    description: "Light and breezy for sunny days.",
    image: "https://www.okabashi.com/cdn/shop/files/Surf_Elemental_Blue.jpg?v=1749488646&width=1080",
    badge: "",
    price: 30,
    discount: 50,
    stock: 20,
    tags: ["Summer", "Casual"]
  }
])

const handleBuy = (productId) => {
  const product = products.value.find(p => p.id === productId)
  if (product && product.stock > 0) {
    product.stock--
  }
}

const totalStock = computed(() =>
  products.value.reduce((sum, p) => sum + p.stock, 0)
)
</script>

<template>
  <NavBar :totalStock="totalStock" />
  <RouterView :products="products" @buy="handleBuy" />
</template>