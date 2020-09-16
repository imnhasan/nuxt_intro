<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg h-64 w-64 mt-4 bg-gradient-to-r from-purple-100 via-pink-100 to-red-200">
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">Joke</div>
      <p class="text-base">
        {{ joke }}
      </p>
    </div>
    <div class="px-6 pt-4 pb-2">
      <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold bg-gradient-to-r from-red-500 mr-2 mb-2">#joke</span>
      <nuxt-link :to="'/jokes/' + id">
        <span class="float-right inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold mr-2 mb-2 ">GO</span>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Joke',
  props: ['id', 'joke'],
}
</script>
