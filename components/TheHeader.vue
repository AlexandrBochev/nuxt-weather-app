<template>
  <h2 class="mb-2">Weather App</h2>
  <nav class="mb-8">
    <NuxtLink v-for="city of citys" :key="city.id" :to="city.link" class="m-1 py-1 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75">
      {{city.name}}
    </NuxtLink>
  </nav>
</template>

<script setup>
  const citys = [
    {id: 1, name: 'Kyiv', link: '/'},
    {id: 2, name: 'Kharkiv', link: '/kharkiv'},
    {id: 3, name: 'Lviv', link: '/lviv'},
    {id: 4, name: 'Odessa', link: '/odessa'},
    {id: 5, name: 'Kherson', link: '/kherson'},
  ]
</script>