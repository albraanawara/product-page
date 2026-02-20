<template>
  <div>
    <h3 class="text-xl font-bold mb-4">Related Products</h3>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div v-for="item in products" :key="item.id" class="card bg-base-100 shadow">
        <figure><img :src="item.image" /></figure>
        <div class="card-body text-center">
          <h4 class="font-semibold">{{ item.name }}</h4>
          <div>
            <span v-if="item.discount > 0" class="line-through text-gray-400 mr-2">${{ item.price }}</span>
            <span class="font-bold">${{ calculateDiscount(item.price, item.discount) }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['products'],
  methods: {
    calculateDiscount(price, discount) {
      return price - (price * discount) / 100;
    }
  }
}
</script>
