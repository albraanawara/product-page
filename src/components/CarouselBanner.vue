<script setup>
import { onMounted, onUnmounted } from 'vue'

onMounted(() => console.log("CarouselBanner mounted"))
onUnmounted(() => console.log("CarouselBanner unmounted"))
</script>

<template>
  <div class="carousel w-full h-64">
    <div class="carousel-item w-full">
      <img src="https://cdn.clothbase.com/uploads/4734bf57-d2e8-4345-8947-574e85d9039a/beige-cozy-sneakers.jpg" class="w-full" />
    </div>
    <div class="carousel-item w-full">
      <img src="https://contents.mediadecathlon.com/p3064111/k$d9be965d40017be5509e327b0ecff4ed/jogflow-1901-men-s-running-shoes-blackslashgrey.jpg" class="w-full" />
    </div>
    <div class="carousel-item w-full">
      <img src="https://m.media-amazon.com/images/I/71YDLDU709L._AC_UY900_.jpg" class="w-full" />
    </div>
  </div>
</template>