<template>
  <header class="bg-base-200 shadow-md">
    <div class="max-w-6xl mx-auto flex justify-between items-center p-4">
      <div class="text-xl font-bold text-primary">CozyStore</div>

      <nav class="hidden md:flex gap-6">
        <a href="#">Home</a>
        <a href="#">Products</a>
        <a href="#">About</a>
        <a href="#">Contact</a>
      </nav>

      <div class="flex items-center gap-2">
        <button class="btn btn-sm btn-outline">Login</button>
        <button class="btn btn-sm btn-primary">Sign Up</button>
      </div>

      <button class="md:hidden btn btn-square btn-ghost" @click="menuOpen = !menuOpen">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none"
             viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"/>
        </svg>
      </button>
    </div>

    <div v-if="menuOpen" class="md:hidden bg-base-100 shadow-inner">
      <nav class="flex flex-col p-4 gap-2">
        <a href="#">Home</a>
        <a href="#">Products</a>
        <a href="#">About</a>
        <a href="#">Contact</a>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() { return { menuOpen: false } }
}
</script>
