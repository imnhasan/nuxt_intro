<template>
  <div class="bg-gray-500 font-semisolid">
    <div class="container mx-auto flex justify-between item-center py-6">
      <nuxt-link to="/" class="text-white">Home</nuxt-link>
      <div class="flex">
        <nuxt-link to="/jokes" class="ml-16">Jokes</nuxt-link>
        <nuxt-link to="/about" class="ml-16">About</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppHeader',
}
</script>
