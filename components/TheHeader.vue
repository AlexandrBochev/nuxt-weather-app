<template>
  <div class="w-full py-8">
    <h2 class="mb-2">Weather App</h2>
    <nav class="flex flex-wrap">
      <NuxtLink v-for="city of citys" :key="city.id" :to="city.link" class="mr-2 mb-2 py-1 px-5 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75">
        {{city.name}}
      </NuxtLink >
    </nav>
  </div>
</template>

<script setup>
  const citys = [
    {id: 1, name: 'Kyiv', link: '/'},
    {id: 2, name: 'Kharkiv', link: '/kharkiv'},
    {id: 3, name: 'Lviv', link: '/lviv'},
    {id: 4, name: 'Odesa', link: '/odesa'},
  ]
</script>